# String 클래스
- 문자열을 편리하게 다룰 수 있는 String 클래스 사용
- 참조형 클래스
- String 클래스는 개발자가 직접 다루기 불편한 char[]을 내부에 감추고 개발자가 편리하게 문자열을 다룰 수 있도록 다양한 기능을 제공
    - 자바 9 이후부터 char[] 대신 byte[] 사용
      (char는 2byte 차지하는데 영어나 문자는 1byte로 표현 가능해서 영어나 문자는 1byte를 사용하고 그렇지 않을 경우 2byte를 사용 ⇒ 더 메모리를 효율적으로 사용)
- 자바에서 문자열 더할 때, +나 concat 연산자 사용

- 문자열 리터럴을 사용하는 경우 자바는 메모리 효율성과 성능 최적화를 위해 문자열 풀을 사용한다.
- 문자열 리터럴 hello의 경우, 문자열 생성 시점에 같은 값이 있으면 중복하여 만들지 않고, 같은 값을 반환
- 문자열 풀 덕분에 문자열을 사용하는 경우 메모리 사용을 줄이고 문자를 만드는 시간도 줄어들기 때문에 성능도 최적화할 수 있다.

    ```java
    String str1 = new String("hello");
    String str2 = new String("hello");
    System.out.println("new String == 비교 " + (str1 == str2)); //false
    System.out.println("new String equals 비교 " + (str1.equals(str2))); //true
    
    String str3 = "hello";
    String str4 = "hello";
    System.out.println("리터럴 == 비교 " + (str3 == str4)); //true
    System.out.println("리터럴 비교 " + (str3.equals(str4))); //true
    ```

- String은 불변 객체다
    - `String.concat()` 메서드를 사용하면 기존 문자열에 새 문자열을 연결하여 합칠 수 있다.
    - 불변 객체가 값을 변경하는 방법은 새 객체를 만들어 변경된 값을 담는 것이다. concat도 그런 기능
    - String은 불변으로 만들어져서 str3을 변경하면 같은 참조값을 가진 str4가 모르는새 같이 변경되는 사이드이펙트가 발생하지 않는다.
