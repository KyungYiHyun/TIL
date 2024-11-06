# 불변 객체

### 기본형과 참조형의 공유

- **기본형**: 하나의 값을 여러 변수에서 절대로 공유하지 않는다.

- **참조형**: 하나의 객체를 참조값을 통해 여러 변수에서 공유할 수 있다.

- 참조형의 경우에 참조값을 새로운 값에 대입하면 값을 복사해서 대입하게 된다. 따라서 두 변수가 같은 참조값을 가지게되기 때문에 하나의 값을 변경하면 다른 하나의 값도 같이 바뀌게 된다.

### 공유 참조와 사이드 이펙트

- 사이드 이펙트 : 프로그래밍에서 어떤 계산이 주된 작업 외에 추가적인 부수 효과를 일으키는 것을 말한다.

```
package lang.immutable.address;
 public class RefMain1_3 {
 public static void main(String[] args) {
 Address a = new Address("서울");
 Address b = a;
 System.out.println("a = " + a);
System.out.println("b = " + b);
 change(b, "부산");
 System.out.println("a = " + a);
 System.out.println("b = " + b);
    }
 private static void change(Address address, String changeAddress) {
 System.out.println("주소 값을 변경합니다 -> " + changeAddress);
        address.setValue(changeAddress);
    }
 }
```

- 위와 같은 코드에서 ```change``` 메서드에 대해서 잘 모른 상태로 메서드를 사용하게 된다면 ```a```값이 함께 부산으로 변경된 이유를 찾기 어렵다.
- 이와 같이 여러 변수가 하나의 객체를 참조하는 공유 참조를 막을 방법은 없다. 그렇다면 공유 참조로 인해 발생하는 문제를 어떻게 해결할 수 있을까?
