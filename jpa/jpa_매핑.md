
`spring.jpa.hibernate.ddl-auto=create`
JPA는 데이터베이스 스키마를 자동으로 생성하는 기능을 지원한다

```
create: 기존 테이블 삭제 후 다시 생성 (DROP + CREATE)
create-drop: create와 같으나 종료시점에 테이블 DROP
update: 변경된 부분만 반영 (운영 DB에 사용하면 안됌)
validate: entity와 table이 정상 매핑되었는지만 확인
none: 사용하지 않음
```

### 데이터베이스 스키마 자동 생성하기 주의
운영장비에는 절대 create, create-drop, update 사용하면 안됨
개발 초기 단계는 create 또는 update 
테스트 서버는 update 또는 validate
스테이징과 운영서버는 validate 또는 none

### 매핑 어노테이션
```
@Entity // (1) 엔티티 클래스임을 지정하며 테이블과 매핑
@Table(name = "station") // (2) 클래스 이름 지정 
public class Station {
    @Id // (3) 식별값
    @GeneratedValue(strategy = GenerationType.IDENTITY) // (4) pk 생성 규칙
    private Long id;

    @Column(name = "name", nullable = false) // (5) 컬럼 이름 및 속성 매핑
    private String name;
    
    protected Station() { // (6) 매개 변수가 없는 생성자를 선언해주어야한다.
    }
}
```

@Column 
@Temporal
@Enumerated
@Lob
@Transient

### 식별자 매핑

- @Id(직접매핑)
- IDENTITY : 데이터베이스에 위임, MYSQL
- SEQUENCE : 데이터베이스 시퀀스 오브젝트 사용, ORACLE
- TABLE : 키 생성용 테이블 사용, 모든 DB에서 사용
- AUTO : 방언에 따라 자동 지정, 기본값


### 권장하는 식별자 전략
- 기본 키 제약 조건 : NULL 아님, 유일 , 변하면 안된다.
- 미래까지 이 조건을 만족하는 자연키는 찾기 어렵다. 대리키를 사용
- 예를 들어 주민등록번호도 기본 키로 적절하지 않다
- 권장 : LONG + 대체키 + 키 생성전략 사용

-------------------
```
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.show-sql=true
```
DDL 출력
