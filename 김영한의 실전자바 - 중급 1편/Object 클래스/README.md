# Object 클래스

### java.lang 패키지

- 자바 언어를 기루는 가장 기본이 되는 클래스들을 보관하는 패키지

- ```Object``` ,```String``` ,```Integer, Long, Double``` , ```Class``` ,```System```

- import 생략가능

### Object 클래스

- 자바에서 부모가 없으면 묵시적으로 ```Object``` 클래스를 상속받는다.

![image](https://github.com/user-attachments/assets/ff755cb2-6de9-4f9d-9634-34ed95b648f5)

#### Object 클래스가 최상위 부모 클래스인 이유

- ```Object```는 모든 객체에 필요한 공통 기능을 제공한다. ```Object``` 는 최상위 부모 클래스이기 때문에 모든 객체는 기능(```toString(), equals(), getClass()```등을 편리하게 제공(상속) 받을 수 있다.

- ```Object```는 모든 클래스의 부모 클래스이므로, 모든 객체를 다 담을 수 있다. 타입이 다른 객체들을 어딘가에 보관해야 한다면 ```Object``` 에 보관하면 된다.

### Object 다형성

![image](https://github.com/user-attachments/assets/50223d73-1c26-47f2-a92c-0f28272f9223)

```
action(dog) //main에서 dog 전달
private static void action(Object obj) {
 obj.sound(); //컴파일 오류, Object는 sound()가 없다.
}
```

- 위와 같이 ```action``` 메서드 안에서 ```obj.sound()``` 를 호출하면 오류가 발생한다. 왜냐하면 ```obj```는 ```Object``` 타입이고, ```sound()``` 메서드가 없기 때문이다.

![image](https://github.com/user-attachments/assets/48a4b40f-94fd-4524-b6fe-749613e2fdfb)

- 따라서 ```Dog``` 인스턴스의 ```sound()``` 를 호출하려면 다음과 같이 다운캐스팅을 해야한다.
  
  ```
  if (obj instanceof Dog dog) {
  dog.sound();
  }
  ```

![](C:\Users\SSAFY\AppData\Roaming\marktext\images\2024-11-04-11-38-03-image.png)

- ```Object obj``` 의 참조값을 ```Dog dog``` 로 다운캐스팅 하면서 전달한다.

- ```dog.sound()``` 를 호출하면 ```Dog``` 타입에서 ```sound()``` 를 찾아서 호출한다.

#### Object를 활용한 다형성의 한계

- ```Object``` 에 속하지 않은 메서드들을 호출하기 위해서는 다운 캐스팅을 활용해야한다. 즉 다형적 참조는 가능하짐나 메서드 오버라이딩이 안되기 때문에 다형성을 활용하기에는 한계가 있다.



### Object 배열

- ```Object``` 는 모든 타입의 객체를 담을 수 있다. 따라서 ```Object[]``` 를 만들면 세상의 모든 객체를 담을 수 있는 배열을 만들 수 있다. 

```
public class ObjectPolyExample2 {
 public static void main(String[] args) {
 Dog dog = new Dog();
 Car car = new Car();
 Object object = new Object(); //Object 인스턴스도 만들 수 있다.
 Object[] objects = {dog, car, object};
 size(objects);
 }
 private static void size(Object[] objects) {
 System.out.println("전달된 객체의 수는: " + objects.length);
 }
}
```

- ```size()``` 메서드는 ```Object``` 타입만 사용하고, ```Object``` 타입의 배열은 세상의 모든 객체를 담을 수 있기 때문에 지금 만든 ```size()``` 메서드는 자바를 사용하는 곳이라면 어디든지 사용될 수 있다.
  
  ```
