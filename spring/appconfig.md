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

---
### IoC 제어의 역전
- 기존엔 클라이언트 구현 객체가 필요한 객체를 스스로 생성하여 연결, 실행했다.
- 그러나 AppConfig를 사용하면서 구현 객체는 자신의 로직만을 실행하고 다른 필요한 객체를 생성하여 연결해주는 작업을 AppConfig가 대신한다.
- 프로그램 실행흐름을 직접 제어하는 것이 아니라 외부에서 이를 관리해주는 것이 제어의 역전이다.

### DI 의존성 주입
- 정적인 클래스 의존관계
  - OrderServiceImpl은 MemberRepository와 DiscountPolicy를 의존하고 있다.
  - 하지만 실제로 OrderServiceImpl의 의존관계에 어떤 객체가 주입될지는 알 수 없다.
- 동적인 객체 의존관계
  - 애플리케이션 실행 시점에 실제 생성된 객체 인스턴스의 참조가 연결된 의존 관계다.
  - 애플리케이션 실행 시점에 외부에서 실제 구현 객체 생성해서 클라이언트에 전달해 클라이언트와 서버 간의 실제 의존관계가 연결되는 것을 의존관계 주입이라고 한다.
  - 의존관계 주입을 사용하면 클라이언트 코드를 변경하지 않고, 클라이언트가 변경하는 대상의 타입 인스턴스를 변경할 수 있다.
  - 의존관계 주입을 사용하면 정적인 클래스 의존관계를 변경하지 않고, 동적은 객체 의존관계를 변경할 수 있다.
