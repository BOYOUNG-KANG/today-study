# Wrapper class

### 기본형 타입의 한계
- 자바는 객체지향 언어이지만 기본형 타입(int, double)은 객체가 아니기 때문에 한계가 있다.
- 기본형 타입은 객체가 아니므로 메서드를 제공할 수 없다. 객체 참조가 필요한 컬렉션 프레임워크를 사용할 수 없다. 제네릭도 사용할 수 없다.
- 기본형 타입은 null 값을 가질 수 없다.

### 래퍼 클래스 (Wrapper class)
- 기본형 타입을 감싸서 만든 클래스
- 자바는 기본형에 대응하는 래퍼 클래스를 기본으로 제공한다.
    - Byte, Short, Integer, Float …
- 자바가 제공하는 기본 래퍼 클래스는 불변이고, equals로 비교해야 한다.
- new Integer()는 후에 제거될 예정이라 직접 사용하면 안된다.
- Integer.valueOf() 사용
  (자주 사용하는 -128~127 범위 Integer 클래스를 미리 생성하는 방식으로 성능 최적화)
- `intValue` : wrapper 클래스에 있는 기본형 값을 다시 꺼내는 메서드

## 오토 박싱 (Autoboxing)
- 자바 1.5부터 오토 박싱과 오토 언박싱 기능 지원
- auto boxing : primitive type → wrapper class
- auto unboxing : wrapper class → primitive type
    ```java
    int value = 7;
    Integer boxedValue = value; //auto boxing
    int unboxedValue = boxedValue //auto unboxing
    ```
- wrapper 클래스의 연산이 기본형 타입 연산보다 시간이 더 많이 걸린다.

