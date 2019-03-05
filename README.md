# neo4j-korean-analyzer-plugin
neo4j 에서 사용하기 위한 lucene nori analyzer

## 환경
* Neo4j 3.5.1
* Java 1.8 Version
* maven 3

## Build 및 실행
### lucene 5.5버전의 nori analyzer를 build
* git clone https://github.com/Gyunstorys/nori-analyzer-lucene-5.5
* mvn install
* .target/ 내에 있는 lucene-analyzer-nori-1.0-SNAPSHOT.jar -> neo4j/lib디렉토리에 복사

### neo4j korean analyzer plugin build
* git clone https://github.com/Gyunstorys/neo4j-korean-analyzer-plugin
* mvn install
* .target/내에 있는 nori-analyzer-plugin-3.5.1-SNAPSHOT.jar -> neo4j/plugin디렉토리/  복사 
* neo4j 재기동 후 log디렉토리에 debug.log 확인하여 error없이 기동되었는지 확인

## Cypher query를 통해 색인 후 
* CALL db.index.fulltext.listAvailableAnalyzers 실행 후 korean analyzer가 추가 되었는지 확인
* CALL db.index.fulltext.createNodeIndex('색인명', ['label명'], ['property이름'], {analyzer: "korean"})
* CALL db.index.fulltext.queryNodes('색인명','query syntax(검색어)') yield node MATCH(node) return node
* query syntax는 https://lucene.apache.org/core/2_9_4/queryparsersyntax.html 여기서 

