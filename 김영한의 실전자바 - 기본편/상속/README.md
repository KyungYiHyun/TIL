# 상속

## 상속이란?

- 기존 클래스의 속성과 기능을 그대로 물려받는 것, extends 키워드를 사용하면 된다.

## 

## 상속과 메모리 구조

![상속](https://github.com/user-attachments/assets/74528e0a-670d-4b0e-8ab0-fffac6641bc7)

- 자식 인스턴스(Electric Car)가 생성되면 부모(Car)까지 함께 포함해서 인스턴스가 생성된다. 참조값은 x001 하나이지만 실제로 그 안에는 부모와, 자식 클래스정보가 공존하게 된다.

![222](https://github.com/user-attachments/assets/8472e074-6cc9-49d0-8e30-89f6031ff912)

- 특정 함수를 호출하면 **호출하는 변수의 타입을 기준으로** 어떤 함수를 호출할지 결정한다.

- 선언된 타입으로 함수를 찾고 본인 클래스에 함수가 없다면 부모 타입으로 올라가서 찾고 기능을 찾지 못하면 컴파일 오류가 발생한다.

## 상속과 메서드 오버라이딩

### 오버라이딩이란?

- 부모에게서 상속 받은 기능을 자식이 재정의 하는 것을 메서드 **오버라이딩(Overriding)** 이라 한다.

- 오버라이딩 된 메서드는 @Override 애노테이션을 붙여준다. 컴파일러가 이 애노테이션을 보고 메서드가 오버라딩 조건을 만족시키지 않으면 컴파일 에러를 발생시킨다.

## 메서드 오버라이딩 조건

- **메서드이름**이 같아야 한다.

- **메서드 매개변수**의 타입, 순서, 개수가 같아야 한다.

- **반환타입**이 같아야 한다.

- 상위 클래스의 접근제어자보다 더 제한적이어서는 안된다.

- **생성자**는 오버라이딩 할 수 없다.

## super

- 자식 클래스에서 부모를 참조할 수 있는 키워드이다.

## super - 생성자

- 자식 인스턴스를 생성하면 메모리 내부에 자식과 부모 클래스가 각각 만들어지기 때문에 각각의 생성자도 모두 호출되어야 한다.

- **상속 관계를 사용하면 자식 클래스의 생성자에서 부모 클래스의 생성자를 반드시 호출해야 한다.**

- 상속 관계에서 자식 클래스의 생서자 첫줄에 반드시 ``super(...)`` 을 호출해야  한다. 단 기본 생성자```super()``` 인 경우 생략할 수 있다.

- 자식 생성자에 ```super(...)``` 가 없다면 부모 클래스의 인자없는 생성자가 실행되며, 부모 클래스에 인자없는 생성자가 없다면 에러를 발생시키게 된다.
