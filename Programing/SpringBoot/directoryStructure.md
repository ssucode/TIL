# 스프링부트의 디렉토리(패키지) 구조와 역할

### Model(또는 Domain 또는 Post … )
* 테이블의 필드가 DB에서 매핑하는 역할을 담당한다.
* DTO가 들어있다.
* Entity Class 등
```Java
...
@Getter
@Setter
@Entity
public clsss user {
  @id
  @GeneratedValue
  private Long id;
  
  @Column
  private String name;
  
  @Column
  prviate String password;
}
...
```

### Repositroy(또는 Persistance)
* 데이터베이스가 연결되는 레파지토리(DAO)
* JpaRepository 상속등

### Service
* 비즈니스 로직이 들어가는 부분(메소드 같은)

### Controller(또는 web)
* 컨트롤러가 붙어있다.
* INPUT에 대한 RETURN
