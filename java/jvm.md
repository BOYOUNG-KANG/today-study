# JVM(Java Virtual Machine)
- 자바를 실행하기 위한 가상 컴퓨터
- 자바가 OS에 종속적이지 않는다는 특징을 가진다. (ONCE WRITE RUN ANYWHERE)
  - 원래 작성한 코드를 bite code로 변환하는 과정에서 각 OS 별로 다르게 코드가 작성되어야 한다.
  - 그러나 자바의 JVM을 사용하면 각 OS 별로 알아서 변환한다.
  - 이제 자바 말고 다른 언어들도 각각의 가상 머신을 이용하기 때문에 더이상 자바만의 강점은 아님

### JDK (Java Development Kit)
- JRE 이외에도 자바 컴파일러(자바 바이트 코드로 번역), 디버거(코드 전반을 살핌), JAR 도구(자바 바이트 코드를 실행하기 위해 JAR로 압축), 프로파일러(성능 모니터링) 등이 포함됨

### JRE  (Java Runtime Environment)
- 자바로 짠 코드를 실행하기 위해선 JRE 설치가 필수
- JVM과 라이브러리 등 포함
- 이전에 JRE만 따로 다운받을 수 있게 해서 자바를 실행만 할 수 있게 하는 방법을 따로 뒀는데,
  이제는 JRE를 포함하고 있는 JDK 전체를 다운받을 수 있게 해서 JRE와 JDK의 경계가 모호해짐
