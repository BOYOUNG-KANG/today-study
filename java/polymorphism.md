# 다형성
- 한 객체가 여러 타입의 객체로 취급될 수 있는 능력
### 다형성 참조
```
public class Parent {
}

public class Child extends Parent {
}

public static void main(String[] args) {
	Parent poly = new Child();
	poly.parentMethod();
	//poly.childMethod(); 컴파일 에러   
}
```
- 부모 타입의 변수가 자식 인스턴스를 참조
- 위 코드의 경우, Parent를 상속 받은 Child 인스턴스가 생성되었다. 따라서 메모리에 Parent 공간과 Child 공간이 모두 생성된다.

=> `new Child();`를 생성해서 메모리에 부모와 자식의 공간을 생성하고, Parent인 poly에 주소값을 둔다.

- 위의 코드처럼 부모는 자식을 담을 수 있지만 반대로는 불가능하다.
- 다형성 참조의 경우, 메서드 실행 시 참조값을 기준으로 메서드를 찾기 때문에 밑에 있는 자식 메서드는 실행할 수 없다.

### 다형성과 캐스팅
- 업캐스팅 : 부모 타입으로 변경
  - `Parent poly = (Parent) new Child();`
  - 업캐스팅은 생략이 가능하고 생략을 권장한다.
  - 다운캐스팅 : 자식 타입으로 변경
    ```
    Child child = (Child) poly;
    child.childMethod();
    ```
    - 참조값이 부모 타입으로 되어 있어 자식 메서드 실행이 불가능할 때 자식 메서드를 실행하기 위해 다운 캐스팅이 필요할 수 있다.
    - 다운캐스팅이 되면 참조값이 자식 타입으로 되어 있어 자식 메서드 실행이 가능하며, 부모 메서드의 경우 자식 공간 내에 메서드가 없으면 부모로 올라가서 부모 메서드 실행이 가능하다.
  
  - 업캐스팅은 생략이 권장되지만, 다운 캐스팅은 생략되지 않는 이유는 **업캐스팅은 안전하지만 다운 캐스팅은 위험하기 때문이다.**
    ```
    Parent parent1 = new Child();
    Child child1 = (Child) parent1;
    child1.childMethod();

    Parent parent2 = new Parent();
    Child child2 = (Parent) parent2;
    // child2.childMethod(); 런타임 오류(ClassCastException)
    ```
    - 업캐스팅은 자식 인스턴스 생성 시, 부모와 자식 공간이 모두 생성된다.
    - 반면 다운 캐스팅은 부모 인스턴스 생성 시, 부모 공간만 생긴 상태에서 자식으로 참조값은 변경하기 때문에 문제가 발생할 수 있다.
      - 위의 코드에서 자식 메서드를 실행할 때 런타임 에러가 발생했다.

### instanceof
- 다형성에서 다형성 참조는 다양한 자식을 대상으로 참조할 수 있기 때문에 이중 어떤 자식을 참조하는지 직관적으로 확인하고 싶을때 사용한다.
- 예를 들어 다운캐스팅을 실행하기 전에 해당 변수가 어떤 인스턴스인지 instanceof를 이용해 확인이 가능하다.
```
public static void main(String[] arg) {
	Parent parent1 = new Parent();
	call(parent1);

	Parent parent2 = new Child();
	call(parent2); //Child 인스턴스 맞음
}

private static void call(Parent parent) {
	parent.parentMethod();
	
	if (parent instanceof Child) {
		System.out.println("Child 인스턴스 맞음");
		Child child = (Child) parent;
		child.childMethod();
	}
}
```
---
### 메서드 오버라이딩
- 오버라이딩이 항상 우선순위를 가진다.
- 상속 관계에서 멤버 변수는 오버라이딩 되지 않지만, 메서드는 오버라이딩된다.
  - value는 현재 내 타입을 기준으로 속성 값 반환
  - 메서드는 현재 내 타입을 기준으로 메서드를 수행하지만, 만약 현재 메서드를 오버라이딩한 메서드가 있다면 그 메서드가 우선순위를 가져 수행된다.
