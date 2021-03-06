> 엔티티 설계 시 주의점

- 실무에서는 `RDBMS`나 `엔티티`를 다대다 관계 `@ManyToMany`로 설정하는 것을 권하지 않음.
- `외래키가 있는 곳`을 `연관관계의 주인`으로 정한다.
  일대다 관계에서 항상 다쪽에 외래키가 존재한다.

      e.g. 자동차 - 바퀴 : 외래키가 있는 바퀴를 연관관계의 주인을 정한다.

- `@Setter` 사용 지양하기, `@Setter`가 모두 열려있으면 변경 포인트가 너무 많아서 유지보수가 어려워짐
- 모든 연관관계는 `지연로딩`으로 설정하기. 특히, 실무에서.
- `즉시로딩(EAGER)`은 예측이 어렵고, 어떤 SQL이 실행될지 추적이 어려움. 특히, JPQL 실행 시 N+1문제 자주 발생
- 연관된 엔티티를 함께 DB에서 조회해야하면 Fetch Join 또는 엔티티 그래프 기능을 사용함

> 테이블 간 관계(매핑)

- `@OneToOne` `@OneToMany` `@ManyToOne` `@ManyToMany` 등으로 지정해줌
- 관계의 주인 클래스는 `@JoinColumn의 name값`을 지정해주고 거울 클래스는 `mappedBy = "주인 변수"`로 설정해줌

  ```java
  @ManyToOne
  @JoinColumn(name = "parent_id")
  private Category parent;

  @OneToMany(mappedBy = "parent")
  private List<Category> child = new ArrayList<>();
  ```

> 컬렉션은 필드에서 초기화하기

- why? null 문제에서 안전함
- hibernate는 엔티티를 영속화할 때, 컬렉션을 감싸서 hibernate가 제공하는 내장 컬렉션으로 변경함

> 테이블과 컬럼명 생성 전략

1. camelCase → underscore
   ```
   // application을 실행하면 다음과 같은 컬럼명으로 테이블이 생성됨
   e.g. memberPoint → member_point
   ```
2. .(점) → \_(underscore)
3. 대문자 → 소문자

- 논리적 생성: 명시적으로 컬럼, 테이블명을 직접 적지 않으면 `ImplicitNamingStrategy ` 사용 / `spring.jpa.hibernate.naming.implicit-strategy`
- 물리명 적용: 모든 논리명에 적용됨. 실제 테이블에 적용하며 username을 usernm 등으로 커스텀 가능 `spring.jpa.hibernate.naming.physical-strategy`
- 스프링 부트 기본 설정

1. `spring.jpa.hibernate.naming.implicit-strategy: org.springframework.boot.orm.jpa.hibernate.SpringImplicitNamingStrategy`
2. `spring.jpa.hibernate.naming.physical-strategy org.springframework.boot.orm.jpa.hibernate.SpringPhysicalNamingStrategy`

> cascade = CascadeType.ALL

- `persist()` 메서드로 개별적으로 일일히 저장해야했던 것들을 위와 같은 설정을 통해 객체 하나만으로도 한번에 저장될 수 있도록 함.
