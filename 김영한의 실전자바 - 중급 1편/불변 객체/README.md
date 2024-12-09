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

#### 불변 객체 도입

- 객체의 상태(객체 내부의 값, 필드, 멤버 변수)가 변하지 않는 객체를 불변 객체(Immutable Object)라 한다. 
  
  ```
  public class ImmutableAddress {
  private final String value;
  public ImmutableAddress(String value) {
  this.value = value;
    }
  public String getValue() {
  return value;
    }
    @Override
  public String toString() {
  return "Address{" +
  "value='" + value + '\'' +
  '}';
    }
  }
  ```

- 내부 값이 변경되면 안되기 때문에 ```value```의 필드를 ```final```로 선언했다.

- 값을 변경할 수 있는 ```setValue()```를 제거했다.

- 이 클래스는 생성자를 통해서만 값을 설정할 수 있고, 이후에는 값을 변경하는 것이 불가능하다.

##### 정리

- 물론 불변객체가 아니라도 ```new```를 사용해 새로운 인스턴스를 생성할 수도 있지만 중요한 것은 에러가 발생할 수 있는 상황자체를 제거하였다는 점이다. 즉, 불변객체는 값을 변경할 수 없기 때문에 **사이드 이펙트가 원천 차단된다.**
- 

### 불변객체 - 값 변경

```
 public ImmutableObj add(int addValue) {
 int result = value + addValue;
 return new ImmutableObj(result);
 }
```

- 불변객체에서 값을 변경해야 하는 메서드가 필요할 때에는, 새로운 객체를 만들어서 반환한다.
