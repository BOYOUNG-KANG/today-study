# AppConfig

- 생성자를 통해 다른 구현체를 참조하는 방식
- 애플리케이션의 실제 동작에 필요한 구현 객체를 생성한다.
- 생성한 객체 인스턴스의 참조를 생성자를 통해서 주입해준다.
- MemberServiceImpl 입장에서 생성자를 통해서 어떤 구현 객체가 들어오는지 모른다.
- MemberServiceImpl의 생성자를 통해서 어떤 구현 객체를 주입할지는 오직 외부(AppConfig)에서 결정된다.
 
  ```
    public class AppConfig {
     public MemberService memberService() {
     return new MemberServiceImpl(new MemoryMemberRepository());
     }
     public OrderService orderService(){
     return new OrderServiceImpl(new MemoryMemberRepository(), new FixedDiscountRepository());
     }
    }
    ```
