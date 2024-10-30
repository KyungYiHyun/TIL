# 다형성2

## 다형성 활용

- 다형성을 활용하여 코드 중복을 줄일 수 있다.
  
  ![캡처](https://github.com/user-attachments/assets/9137b314-f2c8-452c-afd4-d472a5cc8057)

- 동물 소리를 테스트하는 프로그램에서 각각의 동물 클래스를 만드는 것보다 Animal이라는 클래스를 하나 만들고 동물들이 Animal 클래스를 상속받게 한다.

- Animal 클래스를 상속받고 메서드를 오버라이딩하여 Main 코드에서 Animal 타입으로 각각의 동물 클래스들을 모두 호출할 수 있다.(부모는 자식을 담을 수 있기 때문에)
  
  ```
    // 예시
      public class AnimalPolyMain1 {
     public static void main(String[] args) {
     Dog dog = new Dog();
     Cat cat = new Cat();
     Cw caw = new Caw();
     soundAnimal(dog);
     soundAnimal(cat);
     soundAnimal(caw);
     }
  
    //동물이 추가 되어도 변하지 않는 코드
   private static void soundAnimal(Animal animal) {
   System.out.println("동물 소리 테스트 시작");
   animal.sound();
   System.out.println("동물 소리 테스트 종료");
   }
   }
  ```

- 위와 같이 다형적 참조 덕분에 ```animal``` 변수는 자식인 Dog, Cat, Caw의 인스턴스를 참조할 수 있다.

- 또한 메서드 오버라이딩 덕분에 ```animal.sound()```를 호출해도 ```Dog.sound()```, ```Cat.sound()```, ```Cow.sound()```가 호출된다.

## 추상 클래스1

- 동물(```Animal```)과 같이 부모 클래스는 제공하지만, 실제 생성되면 안되는 클래스를 추상 클래스라 한다.

- 실체인 인스턴스가 존재하지 않고, 상속을 목적으로 사용되며, 부모 클래스 역할을 담당한다.

```abstract class AbstractAnimal {...}```

- 클래스를 선언할 때 ```abstract``` 키워드를 붙여주면 된다.

- ```new AbstractAnimal()``` 과 같이 직접 인스턴스를 생성하지 못한다. 

## 

## 추상 메서드

- 추상 클래스와 비슷하게 추상적인 개념을 제공하는 메서드이다. 따라서 실체가 존재하지 않고, 메서드 바디가 없다.

```public abstract void sound();```

- 추상 클래스와 똑같이 ```abstract``` 키워드를 붙여준다.

- **추상 메서드가 하나라도 있는 클래스는 추상 클래스로 선언해야 한다.**

- **추상 메서드는 상속 받는 자식 클래스가 반드시 오버라이딩 해서 사용해야 한다.**

## 추상 클래스2

**순수 추상 클래스 : 모든 메서드가 추상 메서드인 추상 클래스** 

```
public abstract class AbstractAnimal {
 public abstract void sound();
 public abstract void move();
 }
```

- 코드를 실행할 바디 부분이 전혀 없다.

- 자식은 모든 메서드를 오버라이딩 해야 한다.

- **상속하는 클래스는 모든 메서드를 구현해야 한다.** 

## 인터페이스

- 순수 추상 클래스와 같지만, 약간의 편의 기능이 추가된 기능이다.
  
  ```
    public interface InterfaceAnimal {
   public abstract void sound();
   public abstract void move();
  }
  ```

- ```interface``` 키워드를 사용하면 된다.

- 인터페이스의 메서드는 모두 ```public``` ,```abstract``` 이며 생략이 권장된다.

- 인터페이스는 다중 구현(다중 상속)을 지원한다.
  
  ```
  public class Dog implements InterfaceAnimal {
   @Override
   public void sound() {
   System.out.println("멍멍");
   }
   @Override
   public void move() {
   System.out.println("개 이동");
   }
  }
  ```

- 인터페이스를 상속 받을 때는 ```extends``` 대신에 ```implements``` 라는 구현이라는 키워드를 사용해야 한다.

- **클래스, 추상 클래스, 인터페이스는 프로그램 코드, 메모리 구조상 모두 똑같다.** 

## 상속 vs 구현

- 상속이란 이름 그대로 부모의 기능을 물려받는 기능이다. 하지만 인터페이스는 메서드 이름만 있는 설계도이고, 이 설계도가 실제 어떻게 작동하는지 하위 클래스에서 모두 구현해야 한다. 따라서 인터페이스의 경우 상속이 아니라 해당 인터페이스를 구현한다고 표현한다.

## 인터페이스를 사용해야 하는 이유

#### 왜 순수 추상 클래스가 아닌 인터페이스를 사용해야 할까?

- **제약** : 인터페이스에 있는 메서드는 반드시 구현해야 하기 때문에 제약을 주는 것이다. 반면에 순수 추상 클래스의 경우 실행 가능한 메서드를 끼워 넣을 수 있다. 이렇게 되면 자식 클래스에서 오버라이딩 하지 않는 문제가 발생할 수 있다.

- **다중 구현** : 자바에서 클래스 상속은 부모를 하나만 지정할 수 있다. 반면에 인터페이스는 부모를 여러명 두는 다중 구현(다중 상속)이 가능하다.

**좋은 프로그램은 제약이 있는 프로그램이다.**

## 인터페이스 - 다중 구현

![image](https://github.com/user-attachments/assets/def99049-a0c0-4197-b16a-69b4c8242926)

- 위와 같이 클래스를 다중 상속 하게되면, ```AirplaneCar``` 입장에서 ```move()``` 를 호출할 때 어떤 부모의 ```move()``` 를 사용해야 할지 애매한 문제가 발생한다. 이것을 다이아몬드 문제라 한다. 하지만 인터페이는 모든 메서드가 추상 메서드로 이루어져 있기 때문에 다중 구현이 가능하다.

![image](https://github.com/user-attachments/assets/d18c449a-9347-4e49-8bc7-256268bfad76)

- 위와 같이 ```InterfaceA``` , ```interfaceB``` 는 같은 이름의 ```methodCommon()``` 를 제공하지만 이것의 기능은 ```Child``` 가 구현한다. 그리고 오버라이딩에 의해 어처피 ```Child``` 에 있는 ```methodCommon()``` 이 호출된다. 

- 결과적으로 두 부모의 ```methodCommon()``` 중 선택하는 것이 아니라 그냥 인터페이스들을 구현한 ```Child``` 에 있는 ```methodCommon()``` 이 사용된다. 이러한 이유로 인터페이스는 다이아몬드 문제가 발생하지 않는다.

```
public class Child implements InterfaceA, InterfaceB {
 @Override
 public void methodA() {
 System.out.println("Child.methodA");
 }
 @Override
 public void methodB() {
 System.out.println("Child.methodB");
 }
 @Override
 public void methodCommon() {
 System.out.println("Child.methodCommon");
 }
}
```

- ```implements InterfaceA, InterfaceB``` 와 같이 다중 구현을 할 수 있다.

![image](https://github.com/user-attachments/assets/78ac3ad7-c0f3-46e9-bf59-863ed15ac66c)

- ```a.methodCommon()``` 을 호출하면 ```Child``` 인스턴스를 먼저 찾고, ```InterfaceA``` 타입에서 ```methodCommon()``` 을 찾고 해당 메서드는 ```Child``` 에서 오버라이딩 되어 있기 때문에 ```Child``` 의 ```methodCommon()``` 이 호출된다.

- ```b.methodCommon()``` 을 호출해도 진행과정은 같다.
