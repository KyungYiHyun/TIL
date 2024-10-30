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

-  추상 클래스와 똑같이 ```abstract``` 키워드를 붙여준다.

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

- 








