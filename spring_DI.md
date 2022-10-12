# SPRINGFRAMEWORK DI
## 20221012
### 프로젝트 만들기
- 프로젝트 우클릭> configure> convert to Maven Project
- 메이븐을 통해서 우리 프로젝트에 Spring 라이브러리 세팅
<pre><code><!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.3.18</version>
</dependency>
</pre></code>
- 프로젝트 우클릭> new> 소스폴더> Spring Bean Configuration File
- 객체(bean) 등록하고 스프링 컨테이너 객체 빌드&사용
### 컨테이너 만들기 
<pre><code>ApplicationContext
		context =new GenericXmlApplicationContext("applicationContext.xml");
</pre></code>
- 원래 Object타입으로 반환되는데, 내가 원하는 타입으로 받기 위해 형변환해주기 
<pre><code>
Action action= (Action) context.getBean("Action");
Action action= context.getBean("Action",Action.class);
</pre></code>
- 기본적으로 singleton. lazy-init을 주면 처음 getBean시에 객체 생성된다.
- scope의 기본은 singleton이지만 prototype으로 지정하면 호출할때마다 새것을 만든다.
- 스프링 컨테이너가 만들어 질때 빈 객체를 만듦.
<pre><code> <bean class="com.ssafy.ws.Action" id="action"></bean>
	<bean class="com.ssafy.ws.Audience" id="audience">
		<constructor-arg name="movie" ref="action"></constructor-arg>
        //생성자로 값을 넣기 위한 것
    </bean>
</pre></code>

