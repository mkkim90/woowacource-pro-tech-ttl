## 영속성 컨텍스트
- 엔티티를 영구 저장하는 환경
- 엔티티 매니저로 엔티티를 저장하거나 조회하면 엔티티 매니저는 영속성 컨텍스트에 엔티티를 보관하고 관리
- 엔티티 매니저는 쓰레드간에 공유하면 안된다
- 모든 데이터 변경은 트랜잭션 안에서 실행
```
- 1차 캐시
- 동일성 보장
- 트랜잭션을 지원하는 쓰기 지연
- 변경 감지
- 지연 로딩
```

### 동일성 보장 

```
assertThat(station1 == station2).isTrue();
```

주소값을 == 이라면 주소값으로 비교하는데 아이디가 같으면 동일성을 보장
그걸 영속성 컨텍스트가 보장해줍니다. ID를 기반으로 동일성을 보장해줍니다. 


### 1차 캐쉬

- 영속 컨텍스트를 통해 @id 기반의 캐시값 조회하여 바로 반환
- 만약 1차 캐시에 없으면 DB를 통해 조회를 하여 1차 캐시에 저장하고 반환한다.

<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/%EC%93%B0%EA%B8%B0%EC%A7%80%EC%97%B0_1.PNG" width="100%"></img><br/>
<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/%EC%93%B0%EA%B8%B0%EC%A7%80%EC%97%B0_2.PNG" width="100%"></img><br/>
<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/%EC%93%B0%EA%B8%B0%EC%A7%80%EC%97%B0_3.PNG" width="100%"></img><br/>

### 트랜잭션을 지원하는 쓰기 지연

- 쓰기 지연 sql 저장소에 INSERT SQL 저장하며 트랜잭션 COMMIT 하는 순간 일괄 저장되는 방식
- @Transactional 범위 내에 커밋하는 순간 영속성 컨텍스트를 데이터베이스에 반영

<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/1%EC%B0%A8%EC%BA%90%EC%89%AC.PNG" width="100%"></img><br/>


### 변경 감지 맛보기
- 엔티티와 스냅샷을 비교하여 변경된 값에 대한 UPDATE SQL을 생성하여 쓰기 지연 SQL 저장소에 저장하여 DB에 반영

<img src="https://github.com/mkkim90/2020-woowacource-pro/blob/main/jpa/%EB%B3%80%EA%B2%BD%EA%B0%90%EC%A7%80_1.PNG" width="100%"></img><br/>

### 지연 로딩



출처

[nextstep](https://edu.nextstep.camp/) 
[자바 ORM 표준 JPA 프로그래밍](http://book.interpark.com/product/BookDisplay.do?_method=detail&sc.prdNo=240925953&gclid=Cj0KCQiA6t6ABhDMARIsAONIYyxiXZYQ0zjTFXd5_mJjQhDWcq1uOjWn3SVSn-QInrzEIE30sZAtDYIaAmAGEALw_wcB)
