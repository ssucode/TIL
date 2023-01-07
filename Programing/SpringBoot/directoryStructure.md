# 스프링부트의 디렉토리(패키지) 구조와 역할

### Model(또는 Domain 또는 Post … )
* 테이블의 필드가 DB에서 매핑하는 역할을 담당한다.
* DTO가 들어있다.
* Entity Class
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
