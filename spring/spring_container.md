# 스프링 컨테이너(ApplicationContext)

- AppConfig를 이용해 개발자가 직접 의존성 주입을 해줬는데, ApplicationContext를 이용하면 스프링에서 관리해준다.
- `@Configuration` : 설정 정보로 사용하는 클래스에 붙인다.
- `@Bean`이 붙은 메서드를 모두 호출하여 반환 객체를 스프링 컨테이너에 등록한다.
- 스프링 컨테이너에 등록된 객체가 스프링 빈
- 스프링 컨테이너를 이용해 필요한 스프링 빈 객체를 찾아야 한다.(applicationContext.getBean())
- `ApplicationContext`는 인터페이스
- `AnnotationConfigApplicationContext` 등의 `ApplicationContext` 구현체가 있다.

