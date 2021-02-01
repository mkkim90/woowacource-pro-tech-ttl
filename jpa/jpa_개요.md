## JPA 개요

### jpa 배경
- 객체 지향 패러다임을 지원 
- 기존 sql을 직접 다룰 때 발생하는 문제점을 해결해줄 수 있다.
	- 반복작업 : 새로운 필드가 추가되면 관련된 sql을 다 수정해야한다.
	- 신뢰성 : 엔티티를 신뢰하고 사용할 수 없다. 
  
**SQL중심적인 개발 -> 불일치 패러다임 해결**

**계층형 아키텍처, 진정한 의미의 계층 분할이 어렵다.**

### jpa란?
- Java Persistence API
- 자바 진영의 ORM 기술 표준

#### ORM은 `Object-relational mapping(객체 관계 매핑)
- 객체는 객체대로 설계
- 관계형 데이터베이스는 관계형 데이터베이스대로 설계
- ORM 프레임워크가 중간에서 매핑
**객체와 RDB 두 기둥위에 있는 기술**

#### JPA는 애플리케이션과 JDBC 사이에서 동작

<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/JPA_JDBCAPI.PNG" width="100%" ></img><br/>
### jpa를 왜 사용해야 할까?
- SQL 중심적인 개발에서 객체 중심으로 개발
- 생산성
- 유지보수
- 패러다임 불일치 해결
- 성능
- 데이터 접근 추상화와 벤더 독립성
- 표준 

### 데이터베이스 방언
- jpa는 특정 데이터베이스에 종속적이지 않은 기술
- 방언 : sql 표준을 지키지 않거나 특정 데이터베이스만의 고유한 기능

<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/JPA_%EB%B0%A9%EC%96%B8.PNG" width="100%" ></img><br/>

---------------------------
출처 : 자바 ORM 표준 JPA 프로그래밍

