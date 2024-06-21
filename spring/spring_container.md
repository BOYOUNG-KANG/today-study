# 스프링 컨테이너(ApplicationContext)

- AppConfig를 이용해 개발자가 직접 의존성 주입을 해줬는데, ApplicationContext를 이용하면 스프링에서 관리해준다.
- `@Configuration` : 설정 정보로 사용하는 클래스에 붙인다.
- `@Bean`이 붙은 메서드를 모두 호출하여 반환 객체를 스프링 컨테이너에 등록한다.
- 스프링 컨테이너에 등록된 객체가 스프링 빈
- 스프링 컨테이너를 이용해 필요한 스프링 빈 객체를 찾아야 한다.(applicationContext.getBean())
- `ApplicationContext`는 인터페이스
- `AnnotationConfigApplicationContext` 등의 `ApplicationContext` 구현체가 있다.

### 스프링 컨테이너 생성 과정

1. 스프링 컨테이너 생성
   - new AnnotationConfigApplicationContext(AppConfig.class)
   - 스프링 빈 저장소를 포함한 스프링 컨테이너를 생성한다.
   - 스프링 컨테이너를 생성할때 구성 정보(AppConfig.class)를 지정해야 한다.
2. 스프링 빈 등록
   - 스프링 컨테이너는 구성 정보(AppConfig.class)를 확인해 스프링 빈을 등록한다.
     *단 빈의 이름은 중복되어서 안된다. 이 경우 설정 상 오류가 발생할 수 있다.
3. 스프링 빈 의존관계 주입
   - 스프링 컨테이너는 설정 정보를 참고해서 의존관계를 주입한다.
   - 따라서 스프링 빈을 등록하면 의존관계 주입까지 한번에 처리된다.
