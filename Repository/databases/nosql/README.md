- [RavenDB](https://ravendb.net/)
- [MongoDB]()
- [Elasticsearch]()
- [Apache Cassandra](https://cassandra.apache.org/_/index.html)

---

## RavenDB



---

## MongoDB

**Quando usar o MongoDB**
- Os dados são documentos ou semiestruturados (por exemplo, JSON, XML) com recursos avançados de consulta.
- Desenvolvimento rápido de aplicativos em que o esquema muda continuamente.
- Grandes dados estruturados são normalizados para várias tabelas SQL e sofrem em termos de desempenho e complexidade.
- Os dados são sem esquema.
- A consistência é preferível à disponibilidade para dados semiestruturados.

**Quando não usar o MongoDB**
- Dados são dados estruturados.
- Os dados são extremamente relacionais (por exemplo, mídias sociais), ou seja, dados semelhantes a gráficos.
- Para Data Warehousing (banco de dados OLAP).
- A gravação multimestre é necessária para cargas pesadas de gravação.
- A alta disponibilidade é preferível à consistência.

**MongoDB As a Service**
- MongoDB Atlas (Global Scaling)
- ScaleGrid MongoDB (Managed MongoDB)
- ApsaraDB for MongoDB

**Alternatives**
- Amazon DynamoDB
- Azure Cosmos DB
- Amazon DocumentDB
- Couchbase
- CouchDB
- Google Cloud Firestore

---

## Elasticsearch

**Quando usar o Elasticsearch**
- É necessária uma pesquisa de texto completo moderada a avançada. 
- A pesquisa de texto completo quase em tempo real é necessária com recursos avançados de aprendizado de máquina (por exemplo, detecção de fraude).
- Motor de busca com suporte a ferramentas avançadas (Kibana, Logstash, Beats).
- Para um grande volume de conjuntos de dados.
- Dados semiestruturados (por exemplo, JSON, Log Data) são usados.

**Quando não usar o Elasticsearch**
- Apenas os recursos básicos de pesquisa de texto são necessários.
- É necessário um banco de dados primário compatível com ACID (Banco de Dados OLTP).
- O conjunto de dados é pequeno e apenas dados estruturados.
- Somente a pesquisa de texto é necessária sem ferramentas sofisticadas (Kibana, Logstash).
- Quando recursos de ponta, mas caros, como aprendizado de máquina avançado, não são um requisito fundamental.

**Elasticsearch As a Service**
- Elastic Cloud (Multi-Cloud)
- Aiven for Elasticsearch (Multi-Cloud)
- Amazon Elasticsearch Service

**Alternatives**
- Apache Solr
- Splunk
- Algolia

---

## Apache Cassandra

**Cassandra As a Service**
- DataStax Astra (Multi-Cloud)
- Aiven for Apache Cassandra (Multi-Cloud)
- Amazon Managed Apache Cassandra Service

**Alternatives**
- HBase
- ScyllaDB
- Azure Cosmos DB
- Google Cloud Bigtable
- Amazon Keyspaces