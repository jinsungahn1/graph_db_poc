# Graph DB POC
## 환경설정
### neo4j 구동
#### Docker
```
version: "3.8"

services:
  neo4j:
    container_name: neo4j-boot
    image: neo4j:5.22.0
    ports:
      - 7474:7474	# for browser console
      - 7687:7687	# for db
    volumes:
      - /mypath/data:/data		## volume mount
    environment:
      - NEO4J_AUTH=neo4j/password
      - NEO4J_ACCEPT_LICENSE_AGREEMENT=yes
      - NEO4JLABS_PLUGINS=["graph-data-science", "apoc"]
      - NEO4J_dbms_security_procedures_whitelist=gds.*, apoc.*
      - NEO4J_dbms_security_procedures_unrestricted=gds.*, apoc.*
```
#### Neo4j Desktop
#### Neo4j Sandbox

## 프로젝트 설명
### Knowledge Graph 생성
#### 1. [langchain_kg_builder.ipynb](langchain_kg_builder.ipynb)
langchain 라이브러리를 사용해서 KG 를 빌드한다.
#### 2. [neo4j_kg_builder_neo4j.ipynb](neo4j_kg_builder_neo4j.ipynb)
neo4j 라이브러리를 사용해서 KG 를 빌드한다.
#### 3. [neo4j_llm_graph_builder.ipynb](neo4j_llm_graph_builder.ipynb)
Neo4j LLM Knowledge Graph Builder 를 사용해서 KG 를 빌드한다.

### Knowledge 조회(Graph RAG)
#### 1. [neo4j_kg_retriever.ipynb](neo4j_kg_retriever.ipynb)[neo4j_kg_retriever.ipynb](neo4j_kg_retriever.ipynb)
Neo4j 라이브러리를 사용해서 KG 를 조회한다.

### Machine Learning
#### 1. [neo4j_node_embedding.ipynb](neo4j_node_embedding.ipynb)
FastRP 알고리즘을 사용해서 node embedding 을 생성 후 조회한다.