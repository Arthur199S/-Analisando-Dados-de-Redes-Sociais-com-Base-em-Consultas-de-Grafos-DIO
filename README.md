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
<img width="1394" height="811" alt="bloom-visualisation (1)" src="https://github.com/user-attachments/assets/d293716b-00e3-4dd1-a4ea-9faa3742b221" />

---

## 📊 Estrutura Atual
- **Nós:** 17  
- **Relacionamentos:** 28  

---

## ⚙️ Tecnologias Utilizadas
- Neo4j (Graph Database)
- Cypher

---

## 🎲 Dados
// ===== USUÁRIOS =====
CREATE (u1:Usuario {Nome: "Arthur", name: "Arthur", Idade: 21})
CREATE (u2:Usuario {Nome: "Carla", name: "Carla", Idade: 23})
CREATE (u3:Usuario {Nome: "João", name: "João", Idade: 25})
CREATE (u4:Usuario {Nome: "Maria", name: "Maria", Idade: 22})
CREATE (u5:Usuario {Nome: "Pedro", name: "Pedro", Idade: 28})

// ===== RELACIONAMENTO: SEGUE =====
CREATE (u1)-[:Segue {Desde: "20/01/2018"}]->(u2)
CREATE (u2)-[:Segue {Desde: "15/03/2019"}]->(u3)
CREATE (u3)-[:Segue {Desde: "10/07/2020"}]->(u4)
CREATE (u4)-[:Segue {Desde: "05/05/2021"}]->(u5)
CREATE (u5)-[:Segue {Desde: "01/01/2022"}]->(u1)

CREATE (u1)-[:Segue]->(u3)
CREATE (u1)-[:Segue]->(u4)
CREATE (u2)-[:Segue]->(u4)
CREATE (u3)-[:Segue]->(u5)

// ===== PUBLICAÇÕES =====
CREATE (p1:Publicacao {Conteudo: "Aprendendo Neo4j 🚀", name: "Post 1", Data: "2024-01-10"})
CREATE (p2:Publicacao {Conteudo: "Grafos são muito poderosos", name: "Post 2", Data: "2024-01-11"})
CREATE (p3:Publicacao {Conteudo: "Estudando banco de dados", name: "Post 3", Data: "2024-01-12"})

// ===== RELACIONAMENTO: FEZ =====
CREATE (u1)-[:Fez]->(p1)
CREATE (u2)-[:Fez]->(p2)
CREATE (u3)-[:Fez]->(p3)

// ===== RELACIONAMENTO: CURTIU =====
CREATE (u2)-[:Curtiu]->(p1)
CREATE (u3)-[:Curtiu]->(p1)
CREATE (u4)-[:Curtiu]->(p1)

CREATE (u1)-[:Curtiu]->(p2)
CREATE (u3)-[:Curtiu]->(p2)

CREATE (u1)-[:Curtiu]->(p3)
CREATE (u2)-[:Curtiu]->(p3)
CREATE (u5)-[:Curtiu]->(p3)

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
