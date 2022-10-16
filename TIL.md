# SPRINGFRAMEWORK DI
## 20221011
**학습목표**
- DI와 IoC에대해 답변하기
- maven을 통해 라이브러리 세팅할 수 있다.
- 스프링 설정파일에 객체등록하기, 의존관계를 생성할 수 있다.
- 컨테이너를 빌드해서 원하는 객체를 받아다 쓸 수 있다.
- - -
### DI(Dependency Injection)
- 의존성 : 어떤 일을 처리하기 위해서 다른 객체의 도움을 받아야만 일을 처리할 수 있다면 의존한다고 표현한다. 
- 의존성 주입 : 사용객체에 대하여 직접 의존성을 생성하는 것이 아니라, 생성자, 팩토리 메서드, setter 등을 이용하여 종속성을 정의한다.
- 종속성에 대한 인스턴스화를 직접 제어하지 않고 이를 역전시키기 때문에 이러한 프로세스를 IoC(제어 역전)이라 한다.
### IoC(Invercion of Control)
- IoC를 적용한 환경에서는 사용할 객체를 직접 생성하지 않고 객체의 생명주기 관리를 외부에 위임한다. 스프링 컨테이너 또는 IoC컨테이너가 사용된다. 객체의 관리를 컨테이너에 맡겨 제어권이 넘어간 것을 제어 역전이라고 부르며, 제어 역전을 통해 의존성 주임, 관점 지향 프로그래밍이 가능해진다.
### Spring IoC Container
- 스프링에서 핵심적인 역할을 하는 객체를 Bean이라고 하며, Container는 Bean의 인스턴스화 조립, 관리한다. 사용과 소멸에 대한 처리를 담당한다.
- BeanFactory : 프레임워크 설정과 기본기능을 제공하는 컨테이너, 모든 유형의 객체를 관리할 수 있는 메커니즘을 제공한다.
- WebApplicationContext : 웹환경에서 Spring을 사용하기 위한 기능. 대표적으로 XmlWebApplicionContext가 있다.
### Bean 생성 및 설정_ xml방식
생성자 base, setter base가 있다.
### Bean 생성 및 설정_ Annotaction 방식
@Component: 객체를 생성할 대상 클래스에 작성해주는 Annotation이다. 
@Autowird: 컨테이너 내에서 타입매칭을 시행해 컨테이너에 해당하는 타입의 bean이 있다면 매칭한다. 
<pre><code>@Component
public class Store {
  @Autowird
    private Item item;
      (...)
}
</code></pre>
스프링 컨테이너 객체생성
<pre><code>ApplicationContext context= new GenericXmlApplicationContext("com/safy/di01/applicationContext.xml");
Store store = context.getBean("store", Store.class);</code></pre>
