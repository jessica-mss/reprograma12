<h1 align="center">
    <br>
    <p align="center">Semana 12 - Introdução ao Banco de Dados<p>
</h1>


## Explicação da atividade
Neste repositório farei um resumo sobre os conceitos aprendidos em relação a banco de dados.


## Banco de dados (db - database)
É uma coleção de dados/informações que juntas fazem algum sentido. 
O banco de dados ajuda a facilitar a consulta dessas informações e também ajuda a manter a segurança e integridade delas.
  - É baseada em esquemas;
  - Forte consistência de dados (estrutura mais rígida);


## DB Relacional
Banco de dados relacional são dados organizados em tabelas e que usam linguagem SQL (Structured Query Language) = Linguagem de Consulta Estruturada


## DB Não Relacional
Banco de dados NÃO relacional não usam linguagem SQL (consulta estruturada) por isso são NoSQL. 
Eles podem ser organizados em gráfos, chave-valor, colunar e documentos JSON.
DB que usam arquivos JSON facilitam o trabalho do DEV porque eles podem manipular o banco de dados utilizando o mesmo formato do documento do código da aplicação.
  - Facilidade de inserção e acesso aos dados;
  - Flexibilidade da estruturação
  - O NoSQL é mais indicado para aqueles sistemas que tenham necessidades maiores de armazenamento e desempenho.

Exemplos de DB NoSQL: 
	chave-valor: redis; **à chave é um string que define o indice e o valor corresponde ao indice
	gráfos: Arangodb;
  colunar: Cassandra
  
  
  ## SGBD (Sistema de Gerenciamento de Banco de Dados)
São softwares usados para gerir os vários banco de dados. O gerenciamento pode ser feito pela alterações dos dados, consultas e permissões de utilização.

Exemplos de SGBD:
  - MySQL;
  - PostgreSQL;
  - SQLServer;
  - MongoDB.
  
  
<h2 align="center">
    <br>
    <p align="center">Let's practice - MongoDB<p>
</h2>

## Demandas + respostas da Atividade

  * Criar um banco de dados novo;
```http
use reprogramaflix
```
  
  * Criar uma coleção;
```http
db.createCollection('series')
```
  
  * Inserção de documentos;
```http
  db.series.insertMany([<arquivo Series.json>]);
```

  * Atualização de documentos;
```http
db.getCollection('series').update(
{"id": "1"},
{$set:{"title": "Game of Thrones - atualizado de acordo com demanda da atividade"}},
{"multi": false}
);
```

  * Exclusão de documentos;
```http
db.series.deleteOne(
{"id":"11"}
);
```

  * Consulta com projeção - Lista de séries de genero "Aventura e "Drama".
```http
 db.getCollection('series').find({'genre':'Aventura', 'Drama'});
 ```
 
  * Consulta utilizando combinação entre os seletores;
```http
 db.getCollection('series').find({'genre':'Romance', 'totalSeasons':{$gt:8}});
 ```

  * Consulta paginada e ordenada (utilizar *skip*, *limit* e *sort*).
 ```http
 db.getCollection('series').find({'categoria':'Crime'}).sort({id:1}).skip(2).limite(1);
 ```
