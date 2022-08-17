# OOP

<details>
<summary>SOLID</summary>
<div markdown="1">       
  
  ## SOLID란? 
  SOLID 원칙이란 확장성과 유지 보수성을 고려한 객체지향 프로그래밍을 위해 지켜야할 5가지 원칙이다.
  - S : Single Responsibility Principle (SRP,단일 책임 원칙)
  - O : Open-Closed Principle (OCP,개방 폐쇄 원칙)
  - L : Liskov Substitution Principle (LSP,리스코프 치환 원칙)
  - I : Interface segregation principle (ISP, 인터페이스 분리 원칙)
  - D : Dependency Inversion Principle (DIP , 의존 역전 원칙)
  
  ### 1. Single Responsibility Principle (SRP,단일 책임 원칙)
  단일 책임 원칙은 하나의 모듈은 하나의 책임만 가져야 하고 변경되는 이유가
  한가지여야 한다는 원칙이다. 변경의 이유가 한가지 라는 것은 해당 모듈이 오직 하나의 
  액터(해당 모듈을 사용하는 다른 모듈)에 대해서만 책임을 가져야 한다는 것을 의미한다.
  
  
  하지만 여기서 여러가지 의문점이 생기는데. 하나의 액터에 대해서만 책임을 가져야 한다면
  하나의 모듈은 하나의 액터만 가져야한다는 말이고 이는 모듈의 재사용성을 강조하는 객체지향과는
  괴리가 있는게 아닐까? 라고 생각했었는데 액터는 단순히 "해당 모듈을 사용하는 다른 모듈"을 의미하는게
  아닌 시스템이 동일한 방식으로 변경되기를 원하는 사용자 집단을 의미한다고 한다.
  해당 개념은 [링크 참고](https://steady-coding.tistory.com/370#%EC%B1%85%EC%9E%84%EC%9D%80_%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C?_-_2)
  
  ### 2. Open-Closed Principle (OCP,개방 폐쇄 원칙)
  
  개방 폐쇄 원칙은 확장(Extension)에는 열려있고 수정(Modification)에는 닫혀있어야 한다라는 원칙입니다.
  즉, 세부 구현을 수정하지않고 기능을 확장시킬수 있는 코드 구조를 지켜야 하는 것을 말한다다.
  
 
  예를 들어 JDBC API의 드라이버의 경우를 생각해보면 각 데이터베이스의 제품군에 맞게 DriverManager를 
  상속받아 구현하여 사용할 수 있다. 이는 확장(DB제품 변경에 따른 세부 구현 커스텀)에는 열려있고 
  수정(JDBC API와 DriverManager의 수정)에는 닫혀있는 구조다. 결국 개방 폐쇄 원칙을 잘 준수
  하기 위해서 필요한 것은 추상화다. 공통적인 부분을 추상화하여 변하는 것들은 숨기고 변하지 않는
  것들에 의존하게 하면 JDBC API의 예시처럼 개방 폐쇄의 원칙을 잘 준수할 수 있다.
  
  ### 3. Liskov Substitution Principle (LSP,리스코프 치환 원칙)
  
  리스코프 치환 원칙은 상위 타입 객체를 하위타입의 객체로 치환해도 프로그램이 정상적으로 동작해야
  한다는 원칙이다. 
  
  ex) 정사각형-직사각형(square extends rectangle)
  모든 정사각형은 직사각형이기 때문에 상속의 논리적 모순(오류)이 없지만 모든 직사각형이 정사각형이
  아니기때문에 상위타입 객체(직사각형)를 하위타입 객체(정사각형)으로 치환했을때 논리적 모순이 발생할 수 있고
  이는 리스코프 치환 원칙을 위배한다.
  
  ### 4. Interface segregation principle (ISP, 인터페이스 분리 원칙)
  인터페이스 하나의 범용 인터페이스 보다 분리 원칙은 특정 클라이언트를 위한 인터페이스 여러개를
  지향해야 한다는 원칙이다.
  
  ```java
  
  // 다수의 범용 인터페이스
  public interface Human{
    playFootball();
    playBaseball();
    cook();
  }
  ```
  
  ``` java 
  // 특정 클라이언트를 위한 여러개의 인터페이스
  public interface FootBallPlayer{
    playFootball();
  }
  public interface BaseBallPlayer{
    playBaseball();
  }
  public interface Chef{
    cook();
  }
 
  ```
  
  ### 5. Dependency Inversion Principle (DIP , 의존 역전 원칙)
  의존 역전 원칙이란 고수준 모듈이 저수준 모듈의 구현에 의존하는 전통적인 의존관계를
  반전(역전) 시킴으로써 고수준 모듈이 저수준 모듈의 구현으로 부터 독립되게 할 수 있게 하는 원칙이다.
  컴파일 시점에서 의존성이 역전된다.
  
  
  ```java
  // 고수준 모듈(Man) 저수준 모듈(Shirt)의 구현에 의존하는 경우 
  // Man은 셔츠밖에 입을 수 없다.
  public class Man{
    int age;
    String name;
    ...
    Shirt shirt;
  }
  
  class Shirt extends Top{
    ....
  }
  
  class T_Shirt extends Top{
    ....
  }
  class Polar extends Top{
    ....
  }
  
  ```
  
  ```java
  // 저수준 모듈이 고수준 모듈에서 정의한 추상타입에 의존한다.
  // Man은 런타임 시점에 여러가지 상의를 입을 수 있다.
  public class Man{
    int age;
    String name;
    ...
    Top top;
  }
  
  class Shirt extends Top{
    ....
  }
  
  class T_Shirt extends Top{
    ....
  }
  class Polar extends Top{
    ....
  }
  
  ```
</div>
</details>
