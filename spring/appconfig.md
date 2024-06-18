# AppConfig

- 생성자를 통해 다른 구현체를 참조하는 방식
- 애플리케이션의 실제 동작에 필요한 구현 객체를 생성한다.
- 생성한 객체 인스턴스의 참조를 생성자를 통해서 주입해준다.
- MemberServiceImpl 입장에서 생성자를 통해서 어떤 구현 객체가 들어오는지 모른다.
- MemberServiceImpl의 생성자를 통해서 어떤 구현 객체를 주입할지는 오직 외부(AppConfig)에서 결정된다.
 
  ```
    public class AppConfig {
     public MemberService memberService() {
         return new MemberServiceImpl(memberRepository());
		}
     public OrderService orderService() {
         return new OrderServiceImpl(
                 memberRepository(),
                 discountPolicy());
		}
     public MemberRepository memberRepository() {
         return new MemoryMemberRepository();
		}
     public DiscountPolicy discountPolicy() {
         return new FixDiscountPolicy();
		}
  }
    ```

### AppConfig를 이용해 SRP, DIP, OCP 해결
  - SRP 단일 책임 원칙
    - 구현 객체를 생성하고 연결하는 책임을 AppConfig가 담당
  - DIP 의존관계 역전 원칙
    - 추상화에 의존해야지 구체화에 의존해선 안된다.
    - AppConfig가 구현 객체를 대신 생성해서 의존성 주입해줌
    - 클라이언트 코드는 추상 인터페이스에만 의존하면, AppConfig가 알아서 생성한 구현 객체를 주입
  - OCP 확장에 열려있고, 변경에 닫혀 있음
    - 클라이언트 코드가 DIP를 잘 지키기 때문에 OCP도 지켜짐
    - AppConfig에서 사용할 구현체를 변경해도 클라이언트 코드는 변경하지 않아도 된다.
    - 소프트웨어 요소를 새롭게 확장해도 사용 영역의 변경은 닫혀 있다.
    