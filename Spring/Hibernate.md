> 정의

- JPA의 새로운 표준 정의로써, EJB 엔티티빈 기술을 대체

> DDL-AUTO

- DBMS 스키마에 대한 행위를 지정하는 옵션

  `create` : SessionFactory가 올라갈 때마다 테이블을 지우고 새로 만듦. SQL문을 별도로 만들어서 데이터를 넣는 용도로도 사용가능

  `create-drop` : `create`와 동일하지만, SessionFactory가 내려가면 해당 테이블을 drop시킴

  `update` : SessionFactory가 올라갈 때 Object를 검사하여 테이블을 alter 시킴. 데이터는 유지됨.

  `validate` : update처럼 Object를 검사하지만, 스키마는 아무것도 건드리지 않고, Object와 스키마의 정보가 다르다면 에러 발생시킴
