> ## 1. RDB(Relational Database, 관계형 데이터베이스)

`MySQL` `Oracle` `PostgreSql` 등이 대표적. 아래 그림처럼 테이블 간 관계를 이루고 있음.

### 특징

- 테이블(Table)마다 스키마(Schema)를 정의해야 한다.
- 데이터 타입과 제약(Constraint)를 통해서 데이터의 정확성을 보장한다.
- SQL 질의문을 통해 요청 처리한다.
- 성능을 높이려면 하드웨어(H/W)를 고성능으로 교체해야 한다.(Scale Up)
- 고성능 하드웨어는 가격이 비싸서, RDB의 성능을 높이거나 확장하기 어렵기 때문에 확장성이 좋지 않다. -참고로 PostreSql은 ORDBMS로 객체-관계 데이터베이스이다.

> ## 2. NoSQL(Not only SQL)
>
> `mongoDB` `hBase`등이 대표적. `mongoDB`의 경우 문서(document)형 데이터베이스이다. `Key-Value`형식으로 나타난다.

### 특징

- RDB의 확장성 이슈를 해결하기 위해 나온 데이터베이스 모델
- 분산 컴퓨팅 활용이 목적이고, 이것을 통해 비교적 저렴한 가격으로 DB 성능을 높일 수 있다.(Scale Out)
- 여러 개의 테이블이 아닌, 큰 테이블 하나만을 사용한다.
- 가장 많이 쓰이는 NoSQL의 방식은 key-value방식으로 데이터를 관리한다.
- SQL 질의문을 사용하지 않는다.
- Schema-less(구조 변경이 용이하고, 데이터 형식이 다양하며, 바꾸기 쉬우며, 정확성 보다는 데이터 양이 중요한 빅데이터(Big Data)에 사용한다.
- 대표적으로 MongoDB(document-oriented), redis(key-value) 등이 있음

> ## 3. In-Memory DB
>
> `NoSQL 방식`에 속하는 데이터베이스이며, `Key-Value 방식`을 사용하고 있다.

### 특징

- Memory의 가격이 용량 대비, 충분히 낮아지면서 빠른 데이터베이스 성능을 위해 등장한 것.
- 디스크(Disk) 대신 메모리(Memory)를 사용함으로써, I/O(input/output)의 성능을 높여준다.
- 대표적으로 Redis 및 LMDB 등이 있다.
