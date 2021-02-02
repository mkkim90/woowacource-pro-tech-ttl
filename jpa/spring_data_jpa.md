## 스프링데이터 jpa 소개
- 지루하게 반복되는 crud 문제를 세련된 방법으로 해결
- 개발자는 인터페이스만 작성
- 스프링 데이터 jpa 가 구현 객체를 동적으로 생성해서 주입


## 적용 후

```
public interface MemberRepository extends JpaRepository<Member, Long> {
  Member findByUsername(String username);
}

public interface ItemRepository extends JpaRepository<Item, Long> {
}
```
## 공통 인터페이스 기능
- jpaRepository 인터페이스 : 공통 CRUD 제공
- 제너릭은 <엔티티, 식별자>로 설정

## 메소드 이름으로 쿼리 생성
- 메서드 이름만으로 jpql 쿼리 생성

```
List<Member> findByName(String username); -> select * from member where name = 'hello'
```

## @Query , JPQL 정의
```
@Query("select m from Member m where m.username =?1")
Member findByUsername(String username, Pageable pageable);
```

출처 
자바 ORM 표준 JPA 
