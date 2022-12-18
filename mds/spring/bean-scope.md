
## Singleton 
- 하나의 Bean 에 대해 IOC 컨테이너에 단 하나의 객체만 존재한다.
  - ‘singleton’ bean은 Spring 컨테이너에서 한 번 생성된다
  - 컨테이너가 사라질 때 bean 도 제거된다.
  - 생성된 하나의 인스턴스는 single beans cache에 저장되고, 해당 bean에 대한 요청과 참조가 있으면 캐시된 객체를 반환한다.
    - 즉, 하나만 생성되기 때문에 동일한 것을 참조한다.
  - 기본적으로 모든 bean은 scope이 명시적으로 지정되지 않으면 singleton이다.

## Prototype
- 하나의 Bean 에 대해 다수의 객체가 있을 수 있다.
- prototype’ bean은 모든 요청에서 새로운 객체를 생성하는 것을 의미한다.
  - 즉, prototype bean은 의존성 관계의 bean에 주입 될 때 새로운 객체가 생성되어 주입된다. 
- 정상적인 방식으로 gc에 의해 bean이 제거된다.


## request
- 하나의 Bean 정의에 대하여 하나의 HTTP request 의 생명주기 안에 단 하나의 객체만 존재한다.
  - 각각의 HTTP request 는 자시만의 객체를 가진다.
- Web-aware Spring ApplicationContext 안에서만 유효하다

## session
- 하나의 Bean 정의에 대해서 하나의 HTTP session 의 생명 주기 안에 단 하나의 객체만 존재한다.
- Web-aware Spring ApplicationContext 안에서만 유효하다

## global session
- 하나의 Bean 정의에 대해서 하나의 global HTTP Sesscion 의 생명주기 안에 단 하나의 객체만 존재한다.
- 일반적으로 portlet context 안에서 유효하다.
- Web-aware Spring ApplicationContext 안에서만 유효하다