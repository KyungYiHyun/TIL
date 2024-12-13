# 열거형 - ENUM

### 문자열과 타입 안정성

회원 등급과 같이 종류가 있는 데이터들을 문자열로 입력받게 되면 다음과 같은 문제가 발생한다.

- **타입 안정성 부족** : 오타가 발생할 수 있고, 유효하지 않은 값이 입력될 수 있다.
- **데이터 일관성** : 소문자와 대문자를 섞어 쓰는 등 다양한 형식으로 문자열을 입력할 수 있다.

즉 데이터를 입력받을 때부터 정해져있는 종류만 입력받도록 클래스를 설계해야한다.

### 타입 안전 열겨형 패턴

- ```enum```은 ```enumeration```의 줄임말고 열거라는 뜻이고 어떤 항목을 나열하는 것을 뜻한다. 

```java
public class ClassGrade {
 public static final ClassGrade BASIC = new ClassGrade();
 public static final ClassGrade GOLD = new ClassGrade();
 public static final ClassGrade DIAMOND = new ClassGrade();
}
```

열거형 패턴을 직접 구현하면 위와 같다.

- 각 회원 등급별로 인스턴스를 생성하고, ```static```사용해 클래스 변수로 만들고, ```final```을 사용해 인스턴스(참조값)을 변경할 수 없게 한다.
- ```ClassGrade``` 타입을 사용할 때는 ```ClassGrade.BASIC```과 같이 사용하면 된다.
- 이와 같은 열거 패턴을 사용해 **타입 안정성**과 **데이터 일관성**을 향상시킬 수 있다.

### 열거형 - Enum Type

자바는 타입 안전 열거형 패턴을 편리하게 사용할 수 있도록 ```Enum Type```을 제공한다.

```java
public enum Grade {
 BASIC, GOLD, DIAMOND
}
```

- ```class```대신 ```enum```을 사용하고, 원하는 상수의 이름을 나열하면 된다.

### 열겨형 - 주요 메서드

- **values()** : 모든 Enum 상수를 포함하는 배열 반환
- **valueOf(String name)** : 주어진 이름과 일치하는 ENUM 상수를 반환한다.
- **name()** : ENUM 상수의 이름을 문자열로 반환한다.
- **ordinal()** : ENUM 상수의 선언순서를 반환한다.(**가급적 사용하지 말 것**)
