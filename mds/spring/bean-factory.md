# BeanFactory 란?

- 스프링 컨테이너의 최상위 컨테이너이다. (인터페이스)
- ApplicationContext 와 함께 스프링 컨테이너라고 한다.
- Bean 의 생성과 설정, 관리 등의 역할을 맡고 있다.
- 직접적으로 생성을 안하고 BeanFactory 를 이용해 만들어 의존성을 낮추어서 유지보수성을 향상시킨다.
- ApplicationContext 는 Beanfactory 의 후손이며 확장이 용이하다. (Facade 패턴)
- Bean 은 스프링 컨테이너가 관리하고 있는 모든 객체를 의미한다.


## ApplicationContext 의 하위 구현체 

- 대표적으로 GenericXmlApplicationContext 라는 클래스가 있다.(XML 설정)
- AnnotaionConfigApplicationContext (@ 어노테이션 설정)이고 스프링 컨테이너라고도 불린다.

- 직접적으로 new 를 이용하여 선언을 하는 것이 아닌 Spring Container 를 이용하여 씀으로써 객체 간의 의존성을 줄일 수 있다.

### XML Bean 등록 방법

- Container는 bean 목록에서 bean을 찾을 때 고유한 이름으로 찾는다.
  - 이 때 id 속성 값을 이용하게 된다. 
  - 만약 id를 생략하게 되면 클래스의 앞글자를 소문자로 하는 naming rule 을 사용하여 자동으로 bean 의 id를 설정한다. 
  - class 속성은 bean으로 만들 객체의 타입을 풀 클래스 이름으로 작성한다.
- 3.0 이전버전에서는 xml 설정을 주로 썼으나 java 설정이 나오고 나서 변경을 하는 추세여서 2가지 방법을 다 알 필요가 있다.

### Java Bean 등록 방법
- bean 을 등록하기 위해서는 @Bean 어노테이션을 이용한다.
- @Bean(name="myName") 혹은 @Bean("myName"을 이용하여 bean 의 id를 설정할 수 있다.
  - 이 때 bean의 이름을 지정하지 않으면 메소드의 이름을 bean 의 id로 자동 인식한다.
    - 메소드 위에 작성하는 bean 어노테이션
    - 메소드의 이름이 Bean 의 아이디가 기본값인데 설정을 하려면 name 을 이용한다.


## ComponentScan 기능을 이용한 bean 등록

### ComponentScan 이란?
  - base-package 로 설정된 경로 하위에 특정 어노테이션을 가지고 있는 클래스를 이용하여 bean 으로 등록한다.

### @Component
- @Component 어노테이션이 작성된 클래스를 인식하여 bean 으로 만들게 되며,
  특수 목적에 따라 세부 기능을 제공하는 @Controller, @Service, @Repository(DAO), @Configuration 등을 인식한다.<br/>
  - @Controller, @Service, @Repository 와 동일한 기능을 가지지만 각 계층을 표현하는 어노테이션은 특정 용도에 맞는 부가적인 혜택이 있으니 계층별로 사용하는 것이 좋다.<br/>
    - @Component : 스프링에서 관리되는 객체(bean)임을 표시하기 위해 사용하는 가장 기본적인 어노테이션이다.
    - @Controller : WebMVC 코드에서 사용되는 어노테이션으로 @RequestMapping 어노테이션은 해당 어노테이션이 작성된 클래스 내에서 사용가능하다.
    - @Service : 비지니스 로직이 작성된 클래스에 사용한다. 추가적인 기능은 없지만 제공할 가능성이 있으니 계층ㅇ을 명시하는것이 좋다.
    - @Repository : 데이터베이스 관련 예외를 포착하여 DataAccessException으로 변환하여 다시 발생시킨다.
    - 기타 계층이 명확하지 않을 때는 @Component 사용