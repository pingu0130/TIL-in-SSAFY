# SPRINGFRAEMWORK MVC
#SPRINGFRAEMWORK MVC
## 20221016
- - -
##### Spring MVC 구성요소
- DispatcherServlet :클라이언트 요청처리
- HandlerMapping: 요청을 어떤 컨트롤러가 처리할 지 결정한다
- Controller: 요청에 따라 수행할 메서드를 선언하고, 요청처리를 위한 로직 수행(비즈니스 로직 호출)
- ModelAndView: 요청처리를 하기 위해서 필요한 혹은 그 결과를 저장하기 위한 객체
- ViewResolver: 컨트롤러에 선언된 뷰 이름을 기반으로 결과를 반환할 뷰를 결정
- View: 응답화면 생성
##### AOP 용어
- Aspect : 여러 클래스에 공통적으로 구현되는 관심사의 모듈화
- Join Point : 메서드 실행이나 예외처리와 같은 프로그램 실행중의 특정 지점, Spring에서는 메서드 실행을 의미한다.
- Advice : 특정 조인포인트에서 Aspect에 의해서 취해진 행동, Around, Before, After 등의 타입이 있다
- Poincut: 조인포인트에 Aspect를 적용하기 위한 조건을 서술한다. Aspect는 지정한 pointcut에 일치하는 모든 조인포인트에서 실행된다.
- Target 객체: 하나 이상의 어드바이스가 적용될 객체. Spring AOP는 Runtime Proxy를 사용하여 구현되므로 객체는 항상 Proxy 객체가 된다.
- AOP Proxy : AOP를 구현하기 위해 AOP 프레임워크에 의해 생성된 객체, Spring Framework에서 AOP프록시는 JDK dyanmic proxy 또는 CGLIB proxy이다.
- Weaving : Aspect를 다른 객체와 연결하여 Advice 객체를 생성한다. 런타임 또는 로딩 시 수행할 수 있지만, Spring AOP는 런타인에 위빙을 수행한다.

