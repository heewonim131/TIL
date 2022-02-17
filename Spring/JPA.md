## JPA (Java Persistence API)
자바 ORM 기술에 대한 명세(자바 애플리케이션에서 관계형 데이터베이스를 사용하는 방식)를 정의한 인터페이스.

- 데이터를 객체지향적으로 관리할 수 있기 때문에 개발자는 비즈니스 로직에 집중할 수 있고 객체 지향적인 개발이 가능하다.
- 자바 객체와 DB 테이블 사이의 매핑 설정을 통해 SQL을 생성한다.
- 객체를 통해 쿼리를 작성할 수 있는 JPQL(Java Persistence Query Language)를 지원한다.
- JPA는 성능 향상을 위해 지연 로딩이나 즉시 로딩과 같은 몇가지 기법을 제공하는데 이것을 잘 활용하면 SQL을 직접 사용하는 것과 유사한 성능을 얻을 수 있다.

## JPA 동작 과정
![image](https://user-images.githubusercontent.com/92259017/154415443-b9e77ff6-d389-480c-8daf-708a66f8169c.png)

JPA는 애플리케이션과 JDBC 사이에서 동작한다.
개발자가 JPA를 사용하면, JPA 내부에서 JDBC API를 사용하여 SQL을 호출하여 DB와 통신한다.

### insert
![image](https://user-images.githubusercontent.com/92259017/154415500-4104596f-4709-4907-82f8-5dcbca4fc8a8.png)

- 개발자는 JPA에 Member 객체를 넘긴다.
- JPA는 
1. Member 엔티티를 분석한다.
2. INSERT SQL을 생성한다.
3. JDBC API를 이용해 SQL을 DB에 전달한다.

### find
![image](https://user-images.githubusercontent.com/92259017/154415610-c4c4eb6f-21d3-45ce-8237-6be8b418f21c.png)

- 개발자는 JPA에 member의 pk 값을 넘긴다.
- JPA는
1. 엔티티의 매핑 정보를 바탕으로 적절한 SELECT SQL을 생성한다.
2. JDBC API를 사용하여 SQL을 DB에 날린다.
3. DB로부터 결과를 받아온다.
4. 결과(ResultSet)를 객체에 모두 매핑한다.
5. 쿼리를 JPA가 만들어 주기 때문에 Object와 RDB 간의 패러다임 불일치를 해결할 수 있다.

## Hibernate (하이버네이트)
자바 언어를 위한 ORM 프레임워크로, JPA 인터페이스를 구현한 구현체의 한 종류.
- 내부적으로 JDBC API를 사용한다. (Hibernate가 지원하는 메서드 내부에서는 JDBC API가 동작하고 있으며, 단지 개발자가 직접 SQL을 직접 작성하지 않을 뿐이다.)
- HQL(Hibernate Query Language)이라 불리는 매우 강력한 쿼리 언어를 포함하고 있다.
