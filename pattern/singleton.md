### 싱글톤 패턴의 단점
- 상속이 불가능 하다.
- 상속 시에 자식 클래스 생성자에서 super 메서드를 이용해 부모 클래스 생성자를 불러오는 방식으로 상속을 받는데 이게 불가능하다. 왜냐면 싱글톤의 클래스 생성자는 private이기 때문에
  - 싱글톤 패턴에서 상속 받는 것을 불가능할때 부모 클래스를 사용하고 싶다면 composite(합성) pattern을 사용해 볼 수 있다.
      - composite pattern
          - 자식 클래스에서 부모 클래스의 객체를 불러 와서 부모 메서드를 사용하는 방식
          - 상속은 부모의 설계도를 가져와서 사용하는 거라면 composite는 부모의 객체를 가져와서 사용하는 방식
          - 상속은 자식 타입을 부모 타입으로 바꿀 수 있는 다형성이 지켜지는데, composite 패턴은 부모 클래스에서 생성한 객체를 불러 와서 사용하는 것이기 때문에 자식을 부모 타입으로 변경할 수 없고, 따라서 클래스 간의 위계를 지킬 수 없다.
            ```
            class Parent {
              private int age;
              private String name;
              private static Parent instance = new Parent();
            
              private Parent(){}
              public static Parent getInstance(){
              return instance;
              }
              void eat(){}
              void sleep(){}
              }
            
              class Child {
              void eat(Parent instance){
              instance.eat();
              }
              void sleep(Parent instance){
              instance.sleep();
              } 
            }
            ```