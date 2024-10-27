# 다형성

## 다형성이란?

- 하나의 객체가 여러 타입의 객체로 취급될 수 있는 능력

# 다형적 참조

#### case1) 부모 타입의 변수가 부모 인스턴스 참조

![11](https://github.com/user-attachments/assets/3f00f946-bf5c-4e7d-b5eb-786d29423559)

- ```Parent parent = new Parent()``` 

- 부모 타입은 Parent를 생성했기 때문에 메모리 상에 Parent만 생성된다.(자식은 생성되지 않는다.)

#### case2) 자식 타입의 변수가 자식 인스턴스 참조

![22](https://github.com/user-attachments/assets/17594602-2ed4-4c6a-b856-26bc47751243)

- ```Child child = new Child()``` 

- 자식 타입인 Child를 생성했기 때문에 메모리 상에 Child와 Parent가 모두 생성된다.

#### case3) 부모 타입의 변수가 자식 인스턴스 참조(중요!)

![333](https://github.com/user-attachments/assets/61630e1c-8419-4407-9fdd-e89f889f955d)

- ```Parent poly = new Child()``` 

- Child 인스턴스를 생성했기 때문에 메모리상에 Child와 Parent가 모두 생성된다.

- 생성된 참조값을 Parent 타입의 변수인 poly에 담아둔다.

- 부모 타입은 자식 타입을 담을 수 있다. (반대는 컴파일 오류 발생)

##### Parent(부모) 타입 변수는 자신인 Parent는 물론이고 자신을 기준으로 모든  자식 타입을 참조할 수 있다. 이것을 바로 다형적 참조라 한다.

## 다형성과 캐스팅

![44](https://github.com/user-attachments/assets/d51a2efd-48f5-4958-8a5d-854e22b496bd)

- 부모 타입 변수인 poly로 childMethod()를 호출했을때 상속 관계는 부모로만 찾아서 올라 갈 수 있기 때문에 자식 타입에 있는 childMethod()를 호출할 수 없다. 따라서 컴파일 오류가 발생한다.

#### 다운캐스팅

- 이 때 부모타입을 자식타입으로 변경하는 다운캐스팅을 할 수 있다.

- ```Child
  Child child = (Child) poly;
  child.childMethod();
  ```

- 위와 같이 부모타입 변수인 poly를 자식타입으로 변경(**다운캐스팅**)하고 child 변수에 대입해 childMethod()를 호출할 수 있다.
  
  ※  정확히는 Parent poly의 타입이 변하는 것이 아니고, 참조값이 Child 타입이 되는 것이다. poly의 타입은 Parent로 그대로 유지된다.

#### 업캐스팅

- 다운캐스팅과 반대로 부모 타입으로 변환할 때 사용한다.

- 생략이 가능하며 매우 자주 사용하기 때문에 생략을 권장한다.

## 다운캐스팅의 주의점

![55](https://github.com/user-attachments/assets/10e12a78-a584-4b4a-9ce4-c66dd5cea2c2)

- Parent 타입으로 Parent 인스턴스를 생성했기 때문에 메모리 상에 자식 타입은 존재하지 않는다.

- ```Child child2 = (Child) parent2``` 이와 같이 다운 캐스팅을 했을 때 메모리 상에 Child가 존재하지 않기 때문에 ```ClassCastException``` 에러가 발생하게 된다.

- 객체를 생성하면 해당 타입의 상위 부모 타입은 모두 생성되기 때문에 업캐스팅의 경우 이런문제가 발생하지 않는다.

## instance of

- ```parent instanceof Child``` 왼쪽이 오른쪽 인스턴스를 참조하는지 아닌지를 true / false로 반환해준다.

- 오른쪽에 있는 타입에 왼쪽에 있는 인스턴스 타입이 들어갈 수 있는지 대입해보면 된다.

## 다형성과 메서드 오버라이딩

![66](https://github.com/user-attachments/assets/10cbcdb2-ea76-44d9-a2de-cb041bd3f0a9)

- 위와 같은 상황에서 Parent 타입의 변수 poly로 poly.value를 호출했을 때 Parent 타입에 있는 value값을 읽는다.

- 하지만 poly.method()를 호출했을 때 자식 타입에서 오버라이딩 된 Child.method()가 실행된다. 즉 **오버라이딩 된 메서드는 항상 우선권을 가진다.**
