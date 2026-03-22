# 📊 Análise de Redes Sociais com Grafos (Neo4j)

## 📌 Descrição
Projeto que utiliza banco de dados em grafo (Neo4j) para modelar e analisar interações em uma rede social.

O objetivo é representar usuários, suas conexões e interações com publicações, permitindo consultas eficientes sobre comportamento social.

---

## 🧠 Modelagem do Grafo

### 🔵 Nós (Nodes)
- `Usuario`
- `Publicacao`

### 🔗 Relacionamentos (Relationships)
- `(:Usuario)-[:Segue]->(:Usuario)`
- `(:Usuario)-[:Curtiu]->(:Publicacao)`
- `(:Usuario)-[:Fez]->(:Publicacao)`

---

## 📷 Visualização do Grafo
<img width="3796" height="1086" alt="Untitled graph (1)" src="https://github.com/user-attachments/assets/846caa19-e89a-4af9-9df1-bfdf999f6c59" />


---

## 📊 Estrutura Atual
- **Nós:** 17  
- **Relacionamentos:** 28  

---

## ⚙️ Tecnologias Utilizadas
- Neo4j (Graph Database)
- Cypher

---

## 🚀 Como Executar

1. Acesse o Neo4j (Desktop ou Aura)
2. Abra o Query Editor
3. Execute os comandos Cypher para criar os dados

---


- `Publicacao`

### 🔗 Relacionamentos (Relationships)
- `(:Usuario)-[:Segue]->(:Usuario)`
- `(:Usuario)-[:Curtiu]->(:Publicacao)`
- `(:Usuario)-[:Fez]->(:Publicacao)`

---

## 📊 Estrutura Atual
- **Nós:** 17  
- **Relacionamentos:** 28  

---

## ⚙️ Tecnologias Utilizadas
- Neo4j (Graph Database)
- Cypher

---

## 🚀 Como Executar

1. Acesse o Neo4j (Desktop ou Aura)
2. Abra o Query Editor
3. Execute os comandos Cypher para criar os dados

---

## 🔍 Consultas Importantes

### 🔎 Quem segue quem
```cypher
MATCH (u1:Usuario)-[:Segue]->(u2:Usuario)
RETURN u1.Nome, u2.Nome
```
🔎 Publicações mais curtidas
```cypher
MATCH (p:Publicacao)<-[c:Curtiu]-()
RETURN p.Conteudo, COUNT(c) AS Likes
ORDER BY Likes DESC
```
🔎 Usuários mais populares (mais seguidores)
```cypher
MATCH (u:Usuario)<-[:Segue]-(seguidores)
RETURN u.Nome, COUNT(seguidores) AS TotalSeguidores
ORDER BY TotalSeguidores DESC
```
🔎 Sugestão de conexão (amigos em comum)
```
MATCH (u:Usuario {Nome: "Arthur"})-[:Segue]->(amigo)-[:Segue]->(sugestao)
WHERE NOT (u)-[:Segue]->(sugestao) AND u <> sugestao
RETURN sugestao.Nome, COUNT(*) AS Forca
ORDER BY Forca DESC
```

📌 Conclusão

Grafos são ideais para modelar redes sociais, pois representam naturalmente conexões e permitem consultas complexas de forma simples e eficiente.
