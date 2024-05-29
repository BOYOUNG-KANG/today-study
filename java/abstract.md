# 추상 클래스
다형성을 공부하다보면 Parent - Child 상속 관계를 구성하고, 각각 클래스가 인스턴스가 생성되는 것은 자연스럽지만, 
Animal - Pig, Cat, Caw 와 같은 관계를 구성하게 되면 Animal은 추상적인 개념인에 Animal 인스턴스가 생성되는 것은 자연스럽지 않다고 느껴진다.

- Animal 처럼 부모 클래스로 제공되지만 실제 인스턴스로 생성되면 안되도록 제약하는 클래스가 추상 클래스다. (`abstract`)
- 상속을 목적으로 제공되고, 부모 클래스 역할을 담당한다.
- 추상 메서드
  - 또한 추상 클래스는 추상 메서드를 생성해서 자식 클래스가 받드시 오버라이딩해야 할 메서드를 강제할 수 있다.
  - 이때 추상 메서드는 메서드 바디가 없고 껍데기만 존재한다.
  - **추상 메서드가 하나라도 있는 클래스는 추상 클래스로 선언해야 한다.**

- 순수 추상 클래스
  - 추상 클래스 내에 모든 메서드가 추상 메서드인 클래스
  - 다형성을 위한 부모 타입 껍데기 역할만 한다.
  - 추상 클래스 내에 모든 메서드가 반드시 추상 메서드만 가능하도록 강제할 수 없다는 한계가 있다.
  - 그런데 `자바의 인스턴스`는 모든 메서드가 추상 메서드만으로 구성되도록 강제할 수 있다.
