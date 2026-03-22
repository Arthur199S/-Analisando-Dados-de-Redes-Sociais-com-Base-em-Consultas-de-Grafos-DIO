
## 📌 Descrição
# -Analisando-Dados-de-Redes-Sociais-com-Base-em-Consultas-de-Grafos-DIO
 Analisando Dados de Redes Sociais com Base em Consultas de Grafos-DIO

---

## 🧠 Modelagem do Grafo

### 🔵 Nós (Nodes)
- `Usuario`
- `Artista`
- `Musica`
- `Genero_de_musica`

### 🔗 Relacionamentos (Relationships)
- `(:Usuario)-[:Segue]->(:Artista)`
- `(:Usuario)-[:Escuta]->(:Musica)`
- `(:Usuario)-[:Gosta]->(:Genero_de_musica)`
- `(:Musica)-[:Pertence]->(:Genero_de_musica)`
- `(:Artista)-[:Criador]->(:Musica)`

---
## 📷 PNGs
<img width="3796" height="1086" alt="Untitled graph (1)" src="https://github.com/user-attachments/assets/2f4512c7-edfd-462f-8fc7-1314dd8f427e" />

---

## 📊 Estrutura Atual
- **Nós:** 17  
- **Relacionamentos:** 28  

---

## ⚙️ Tecnologias Utilizadas
- Neo4j (Graph Database)
- Cypher (linguagem de consulta)

---

## 🚀 Como Executar

1. Acesse o Neo4j (Desktop ou Aura)
2. Abra o Query Editor
3. Execute o script abaixo para popular o banco:

```cypher
// Marshmello
MERGE (n3:Artista {Nome: "Marshmello"})<-[:Segue {Desde: "20/03/2022"}]-(n1:Usuario {Nome: "Arthur"})-[:Escuta {Nota: 10}]->(n2:Musica {`Visualizações`: "22.000.289", Nome_da_musica: "Alone"})-[:Pertence]->(:Genero_de_musica {Genero: "Eletrônica"})<-[:Gosta]-(n1)
MERGE (n3)-[:Criador {`Lançou`: "22/02/2022"}]->(n2)

// Alan Walker
MERGE (a1:Artista {Nome: "Alan Walker"})
MERGE (u1:Usuario {Nome: "Arthur"})
MERGE (m1:Musica {Nome_da_musica: "Faded", `Visualizações`: "3.200.000.000"})
MERGE (g1:Genero_de_musica {Genero: "Eletrônica"})

MERGE (u1)-[:Segue {Desde: "10/01/2023"}]->(a1)
MERGE (u1)-[:Escuta {Nota: 9}]->(m1)
MERGE (m1)-[:Pertence]->(g1)
MERGE (u1)-[:Gosta]->(g1)
MERGE (a1)-[:Criador {`Lançou`: "03/12/2015"}]->(m1)


// The Weeknd
MERGE (a2:Artista {Nome: "The Weeknd"})
MERGE (m2:Musica {Nome_da_musica: "Blinding Lights", `Visualizações`: "4.000.000.000"})
MERGE (g2:Genero_de_musica {Genero: "Pop"})

MERGE (u1)-[:Segue {Desde: "05/06/2022"}]->(a2)
MERGE (u1)-[:Escuta {Nota: 10}]->(m2)
MERGE (m2)-[:Pertence]->(g2)
MERGE (u1)-[:Gosta]->(g2)
MERGE (a2)-[:Criador {`Lançou`: "29/11/2019"}]->(m2)


// Imagine Dragons
MERGE (a3:Artista {Nome: "Imagine Dragons"})
MERGE (m3:Musica {Nome_da_musica: "Believer", `Visualizações`: "2.500.000.000"})
MERGE (g3:Genero_de_musica {Genero: "Rock"})

MERGE (u1)-[:Segue {Desde: "12/08/2021"}]->(a3)
MERGE (u1)-[:Escuta {Nota: 8}]->(m3)
MERGE (m3)-[:Pertence]->(g3)
MERGE (u1)-[:Gosta]->(g3)
MERGE (a3)-[:Criador {`Lançou`: "01/02/2017"}]->(m3)


// Dua Lipa
MERGE (a4:Artista {Nome: "Dua Lipa"})
MERGE (m4:Musica {Nome_da_musica: "Levitating", `Visualizações`: "1.800.000.000"})
MERGE (g4:Genero_de_musica {Genero: "Pop"})

MERGE (u1)-[:Segue {Desde: "20/09/2023"}]->(a4)
MERGE (u1)-[:Escuta {Nota: 9}]->(m4)
MERGE (m4)-[:Pertence]->(g4)
MERGE (u1)-[:Gosta]->(g4)
MERGE (a4)-[:Criador {`Lançou`: "27/03/2020"}]->(m4)


// Coldplay
MERGE (a5:Artista {Nome: "Coldplay"})
MERGE (m5:Musica {Nome_da_musica: "Paradise", `Visualizações`: "1.500.000.000"})
MERGE (g5:Genero_de_musica {Genero: "Alternativo"})

MERGE (u1)-[:Segue {Desde: "01/01/2020"}]->(a5)
MERGE (u1)-[:Escuta {Nota: 7}]->(m5)
MERGE (m5)-[:Pertence]->(g5)
MERGE (u1)-[:Gosta]->(g5)
MERGE (a5)-[:Criador {`Lançou`: "12/09/2011"}]->(m5)
```
