# 스프링부트 디렉토리 구조와 역할
## 구조
Spring Boot는 목적에 따라 패키지를 따로 생성해서 프로젝트를 관리합니다. 
* Controller
* DTO
* Service
* Repository
* Model

## 역할
### Model(또는 Domain 또는 Post … )
* 테이블의 필드가 DB에서 매핑하는 역할을 담당합니다.
* DTO가 들어있습니다.
* 어노테이션은 Entity, Id, Column, Builder 등이 있습니다.
```Java
...
@Entity
@Table(name = "user")
public clsss Users {
  @id
  @GeneratedValue
  private Long id;
  
  @Column
  private String name;
  
  @Column
  prviate String password;
  
  @Builder
  public Users(String name, String password){
    this.name = name;
    this.password = password;
  }
}
...
```

### Repositroy(또는 Persistance)
* DB에 접근하는 소스코드를 모아둔 Interface입니다.
* 데이터베이스가 연결되는 레파지토리(DAO) 입니다.
* JpaRepository interface를 상속받아서 관리하고자 하는 클래스, ID 필드 타입을 `JpaRepository<Entity Class, PK type>` 같이 넣어주면 자동으로 DB와 CRUD 연결을 할 수 있는 메소드를 생성해 줍니다.
```Java
public interface UserRepository extends JpaRepository<Users, Long> {
}
```
### DTO
* Service나 Controller에서 DB에 접근할 때 사용하는 클래스
* Model과 다른점은 Model은 DB 테이블에 대한 정보를 가지고 있는 클래스이고, DTO는 해당 테이블에서 실제로CRUD를 할 필드를 정의해둔 것이 차이점입니다.
```Java
@Getter
@NoArgsConstructor
public class UserSaveRequestDto {
    private String name;
    private String password;
}
```
### Service
* Repository와 DTO를 통해 DB에 접근하여 CRUD의 각각의 프로세스 관리와 예외처리 등을 담당합니다.
* @Service 어노테이션을 붙이면 스프링에서 관리하는 객체가 됩니다.
* 확장성, 재사용성, 중복 코드의 제거를 위해 사용합니다.
* Model과 다른점은 Model은 DB 테이블에 대한 정보를 가지고 있는 클래스이고, DTO는 해당 테이블에서 실제로CRUD를 할 필드를 정의해둔 것이 차이점입니다.
* @Service 어노테이션을 통해 Spring은 beanFactory에 담게 되고, @Autowired를 사용하는 곳에 해당 bean을 찾아 주입합니다.
```Java
@Service
public class UserService {
  @Autowired
  private UserRepository userRepository;
  public User registUser(User user) {
    ...
  }
}
```
### Controller(또는 web)
* Http 요청과 응답을 위한 클래스입니다.
* @Controller 어노테이션을 통하여 bean에 등록되고 스프링에서 관리됩니다.
```Java
@RequestController
@RequestMapping("/")
public class UserController {

    @Autowired
    private UserService userService;

    @PostMapping("")
    public User registUser(@RequestBody User user){
        return userService.registUser(user);
    }
}
```
