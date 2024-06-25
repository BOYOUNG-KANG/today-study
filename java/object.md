# Object 클래스
- 클래스에 상속받을 부모 클래스가 없으면 묵시적으로 Object 클래스를 상속 받는다.
  (`extends Object`)
- 자바 클래스의 최상의 부모 클래스는 항상 Object
    - Child 클래스가 toString() 메서드를 사용할 수 있는 이유(toString은 Object 클래스 메서드)

### 자바에서 Object가 최상위 부모 클래스인 이유
- 공통 기능 제공
  - 모든 객체에게 필요한 공통 기본 기능을 제공
- 다형성의 기본 구현
  - Object 클래스는 다형성을 지원하는 기본적인 메커니즘을 제공
  - 모든 자바 객체는 Object 타입으로 처리될 수 있으며, 이는 다양한 타입의 객체를 통합적으로 처리할 수 있게 한다.

### Object 다형성 한계
- 다형성을 제대로 활용하려면 다형성과 메서드 오버라이딩을 함께 사용해야한다. 이때 Object를 사용한 다형성에는 한계가 있다.
- Object는 모든 객체의 부모이므로 모든 객체를 대상으로 다형성 참조를 할 수 있다. 하지만 Object에는 Dog.sound() 와 같은 객체의 메서드가 정의되어 있지 않아서 메서드 오버라이딩을 사용할 수 없다. 결국 각 기능을 호출하려면 다운 캐스팅을 해야 한다.

### toString
- Object.toString() : Object 객체에서 제공하는 메서드
- 객체 정보를 문자열 형태로 나타낸다.
- 디버깅과 로깅에 유용하게 사용된다.
- 객체의 이름과 참조값을 반환
- `System.out.println`은 내부에서 toString을 호출한다. 따라서 객체를 print하면 toString과 같은 결과

- 만약 객체에서 toString() 클래스를 오버라이딩한다면, println(객체)에도 오버라이딩한 메서드가 적용되어 반환된다.
  - toString 메서드를 재정의 하지 않는 Car 인스턴스는 Object의 toString을 사용하고, toString 메서드를 재정의하는 Dog 인스턴스는 재정의한 메서드를 사용

    ```java
    class Dog {
    	private String name;
    	private int age;
    	
    	public Dog(String name, int age) {
    		this.name = name;
    		this.age = age;
    	}
    
    	@Override
    	public String toString(){
    		return "name = " + name + ", age = " + age;
    	}
    }
    
    class Main {
    	public static void main(String[] args){
    		Car car = new Car();
    		Dog dog1 = new Dog("두부", 1);
    		Dog dog2 = new Dog("시츄", 2);
    		
    		System.out.println(car); //lang.object.toString.Car@3rjk23525
    		System.out.println(dog1); //name = 두부, age = 1
    		System.out.println(dog2);  //name = 시츄, age = 2
    	}
    }
    ```
### OCP
만약 Object와 toString이 없다면 각 객체들 간의 아무 관계가 없고(공통된 부모), 객체의 정보를 출력하기 위해선 각각 객체에서 서로 객체 정보 출력 메서드를 정의했어야 할 것이다. (구체적인 것에 의존)

자바에서 객체 정보를 사용할 때, 다형성 참조 문제를 해결해줄 Object 클래스와 오버라이딩 문제를 해결해줄 Object.toString() 메서드가 있다. (추상적인 것에 의존)

다형성을 잘 활용한다는 것은 다형적 참조와 메서드 오버라이딩을 적절히 사용한다는 것이고, Object와 toString이 이를 돕는다.

- **다형적 참조** : print(Object obj), Object 타입을 매개변수롤 사용해서 다형적 참조를 사용한다. 이렇게 사용하면 Car, Dog 같은 모든 객체 인스턴스를 인수로 받을 수 있다.
- **메서드 오버라이딩** : Object는 모든 클래스의 부모다. Dog, Car과 같은 구체 클래스는 Object가 가지고 있는 toString 메서드를 오버라이딩 할 수 있다. 따라서 print(Object obj) 메서드는 Car, Dog와 같은 구체적인 타입에 의존하지 않고, 추상적인 Object 타입에 의존하면서 런타임에 각 인스턴스의 toString을 호출할 수 있다.

- OCP
  - 새 클래스를 추가해도 toString을 오버라이딩해 기능을 확장할 수 있다.
  - 새 클래스를 추가해도 Object와 toString을 사용하는 클라이언트 코드는 변경하지 않아도 된다.

### System.out.println()
`System.out.println()` 메서드는 Object와 toString을 사용하기 때문에, `System.out.println()`을 사용하여 세상의 모든 객체 정보를 편리하게 출력할 수 있다.
