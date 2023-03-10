---
title: 업무에 사용할 데이터베이스를 검토할때 어떤 부분을 고려해야 하는가?
date: "2023-02-11T22:12:03.284Z"
description: "Hello World"
---

## 업무에 사용할 데이터베이스를 검토할때 어떤 부분을 고려해야 하는가?



### <span style="color:indianred">Scalability</span>

> Scalability 은 애플리케이션에 대한 수요가 증가함에 따라 증가하는 데이터와 사용자를 처리할 수 있는 데이터베이스 관리 시스템의 기능입니다. Scalability 는 데이터베이스를 선택할 때 중요한 고려 사항입니다. 데이터베이스가 시간이 지남에 따라 예상되는 데이터 증가를 수용하고 데이터와 사용자의 양이 증가함에 따라 우수한 성능을 제공할 수 있도록 보장하기 때문입니다.


확장성에는 다음과 같은 여러 가지 유형이 있습니다

#### <span style="color:skyblue">Vertical Scalability</span>
> 기존 서버에 처리 능력이나 스토리지와 같은 리소스를 추가하여 데이터 증가를 수용하는 것을 의미합니다.

#### <span style="color:skyblue">Horizontal Scalability</span>

> 이는 여러 서버에 분산되고 데이터 양을 늘릴 수 있도록 데이터베이스 클러스터에 서버를 추가하는 것을 의미합니다.

#### <span style="color:skyblue">Read Scalability</span>
> 데이터베이스가 성능에 영향을 미치지 않고 쿼리와 같이 증가하는 읽기 작업을 처리할 수 있는 기능을 말합니다.

#### <span style="color:skyblue">Write Scalability</span>
> 이는 데이터베이스가 성능에 영향을 미치지 않고 데이터 삽입, 업데이트 및 삭제와 같이 증가하는 쓰기 작업을 처리할 수 있는 기능을 의미합니다.

확장성이 중요한 이유는 데이터와 사용자의 양이 증가함에 따라 데이터베이스가 지속적으로 우수한 성능을 제공할 수 있도록 지원하기 때문입니다. 또한 확장성이 높은 데이터베이스 관리 시스템은 마이그레이션할 필요 없이 데이터베이스가 시간이 지남에 따라 예상되는 데이터 증가를 수용할 수 있습니다.

**_Postgresql_** 를 포함하여 데이터 증가를 처리하는 데 적합한 여러 데이터베이스 관리 시스템이 있습니다. **_SQL, MySQL_** 및 _**Microsoft SQL Server**_. 이러한 각 데이터베이스에는 고유한 장단점이 있으므로 특정 요구사항을 기준으로 각 데이터베이스를 평가하는 것이 중요합니다.

### <span style="color:indianred">Performance</span>
> 데이터베이스는 데이터 양이 증가하더라도 성능이 우수해야 합니다. 여기에는 데이터베이스의 응답성 뿐만 아니라 쿼리 및 데이터 작업 속도와 같은 요소가 포함됩니다. 
>
> [Database Benchmark Ranking 비교](https://benchant.com/ranking/database-ranking)

Database Performance Metric 종류는 다음과 같습니다.


<span style="color:MediumSlateBlue">

1. Read Latency
2. Write Latency
2. Throughput
4. Concurrency
  
</span>

데이터베이스는 목적성을 가지고 설계되었기에 요구사항에 맞는 데이터베이스 선택이 가능합니다.

예를 들어 위 Metric 중 High Concurrency 가 요구되는 상황이라면?
  - Amazon DynamoDB 및 Google Cloud Bigtable과 같은 데이터베이스는 대규모 동시 워크로드를 처리, 많은 동시 연결을 처리하도록 최적화된 데이터베이스를 선택

Read, Write Latency 를 최우선으로 고려
- Benchmark 결과로 빠른 Latency 를 가지는 Couchbase Server CE v7.0.0 를 고려

높은 Throughput 이 필요하면?
- ScyllaDB v4.5.1 를 고려





### <span style="color:indianred">Data Modeling</span>
> 데이터베이스가 애플리케이션에 필요한 데이터 모델링 접근 방식을 지원하는지? 데이터 간의 복잡한 관계를 저장할 수 있는 기능, 다양한 데이터 유형에 대한 지원, 데이터에 대한 제약 조건을 적용할 수 있는 기능과 같은 요소를 고려합니다.

데이터의 구조에 따라 Database 를 선택하는 것이 중요합니다. 간단히 데이터의 구조에 따른 데이터베이스 유형을 다뤄보겠습니다.

#### <span style="color:skyblue">Relational Database</span>
행과 열이 있는 테이블에 데이터를 저장하고 엄격한 스키마를 적용합니다. 따라서 <span style="color:salmon">표로 쉽게 표현할 수 있는 구조화된 데이터</span>에 적합합니다. 
- MySQL
- PostgreSQL
- Oracle


#### <span style="color:skyblue">NoSQL Database</span>
 <span style="color:salmon">키-값 쌍, 문서 및 그래프 구조를 포함한 다양한 형식의 데이터</span>를 저장합니다. Relational Database 보다 유연한 경우가 많기 때문에 보다 동적이고 비정형적인 데이터를 사용할 수 있습니다. 
- MongoDB
- Cassandra
- CouchDB

#### <span style="color:skyblue">Columnar Database</span>
 행이 아닌 열에 데이터를 저장하므로 데이터를 보다 효율적으로 저장하고 검색할 수 있습니다. 데이터를 집계하여 분석하는 경우가 많은 <span style="color:salmon">빅데이터 및 데이터 웨어하우징 애플리케이션에 적합</span>합니다. 
 - Apache Cassandra
 - HBase

#### <span style="color:skyblue">Time-series Database</span>
TimeStamp 가 찍힌 데이터를 처리하도록 최적화되어 시간 경과에 따른 데이터의 효율적인 저장 및 검색을 가능하게 합니다. <span style="color:salmon">데이터가 높은 빈도로 생성되고 시간이 지남에 따라 분석되는 IoT 및 금융 데이터</span>에 적합합니다. 
- IncludeDB
- TimescaleDB

#### <span style="color:skyblue">Graph Database</span>
데이터를 노드 및 에지로 그래프 구조에 저장하므로 관계가 복잡한 데이터를 효율적으로 저장하고 검색할 수 있습니다. Social Network Data, Recommendation Systems 및 Fraud Detection 에 적합합니다. 
- Neo4j
- Amazon Neptune

각 유형의 데이터베이스에는 고유한 장단점이 있으며, 최선의 선택은 저장되는 데이터의 특정 요구사항과 데이터베이스에 대해 실행되는 쿼리에 따라 달라집니다.

### <span style="color:indianred">Cost</span>

> Licensing, Support, Maintenace 등 포함한 Cost 가 고려되어야 합니다.

### <span style="color:indianred">Ease of Use</span>
> Database 사용성은 매우 중요합니다. 잘 작성된 Document, 유저 친화적 인터페이스, 간편한 배포, 관리를 고려해야 합니다.

### <span style="color:indianred">Interoperability</span>
> 다양한 Program Language 및 Library 유무, Data Exporting, Importing 기능을 고려해봅니다.

### <span style="color:indianred">Community and Support</span>

> Database 의 커뮤니티 활성화 Level 이 추후 운영 간의 필요한 정보를 제공받을 수 있기에 충분히 고려되어야 합니다.

### <span style="color:indianred">Flexibility</span>
> 시간이 지남에 따라 요구사항이 변화는 항상 존재합니다. 따라서 Database 를 확장할 수 있는 기능과 스키마 변경의 용이성과 같은 요소를 고려해야 합니다.


