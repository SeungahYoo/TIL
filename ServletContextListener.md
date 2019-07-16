## Servlet Context Listener

웹 어플리케이션을 실행하는데 필요한 초기화 작업이나 웹 어플레키에션이 종료 된 후 사용된 자원을 반환하는 등의 작업을 수행하는데 사용된다.



웹어플리케이션이 시작되고 종료될 때, 특정한 기능을 실행하려면 다음과 같은 코드를 작성하면 된다.



1. `javax.servlet.ServletcontextListener` 인터페이스를 구현한 클래스를 작성한다.
2. web.xml파일에 1번에서 작성한 클래스를 등록한다.



`ServletContextListener` 인터페이스는 다음 두 개의 메서드가 정의되어 있다.

```java
public void contextInitialized(ServletcontextEvent sce); 
    //웹 어플리케이션이 초기화될 때 호출 된다.
public void contextDestroyed(ServletcontextEvent sce); 
    //웹 어플리케이션이 종료될 때 호출 된다.
```



`ServletContextListener` 인터페이스를 구현한 클래스가 웹 어플리케이션이 시작되거나 종료될 때 실행되도록 하려면 web.xml 파일에 `<listner> `태그와 `<listener-class>` 태그를 사용해서 완전한 클래스 이름을 명시해주면 된다.

- 한 개 이상의 `<listner>` 태그를 등록할 수 있으며, 각 `<listener>`태그에는 반드시 한 개의 `<listener-class>`태그를 자식태그로 가져야 한다.



`ServletContextListener`인터페이스에 정의된 두 메서드는 모두 파라미터로 `javax.servlet.ServletcontextEvent`타입의 객체를 전달 받는데, `ServletContextEvent`클래스는 시작되거나 종료된 웹 어플리케이션 콘텍스트를 구할 수 있는 `getServletcontext()`메서드를 제공하고 있다.



```java
public Servletcontext getServletContext();
```

`getServletContext()`메서드의 리턴값인 `ServletContext`객체는 JSP의 application 기본 객체와 동일한 객체로서, ServletContext객체를 이용하면 web.xml파일에 설정된 어플리케이션 초기화 파라미터를 구할 수 있다.



어플리케이션 초기화 파라미터는 다음과 같이 `<context-param>`태그를 사용하여 web.xml파일에 설정할 수 있다.

```xml
<web-app ...>

    ...

   <context-param>
        <param-name>jdbcdriver</param-name>
        <param-value>com.mysql.jdbc.Driver</param-value>
    </context-param>

    ...

</web-app>

```



- `ServletContext`가 제공하는 초기화 파라미터 관련 메서드

```java
String getInitParameter(String name);
	/* 지정한 이름을 갖는 초기화 파라미터의 값을 리턴한다. 존재하지 않을 경우 null 리턴.
	  name 파라미터에는 <param-name>태그로 지정한 이름을 입력한다. */

java.util.Enumeration getIntParameterNames();
	/* web.xml파일에 정의된 초기화 파라미터의 이름 목록을 Enumeration 타입으로 리턴. */
```





- DB 연동 및 dao 생성에 적용



InitListener.java

```java
public class InitListener implements ServletContextListener {

	@Override
	public void contextInitialized(ServletContextEvent sce) {
		ServletContext context = sce.getServletContext();

		try {
			String driver = context.getInitParameter("jdbcDriver");
			Class.forName(driver);
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
			throw new RuntimeException(e);
		}
	}

	@Override
	public void contextDestroyed(ServletContextEvent sce) {
		ServletContext context = sce.getServletContext();
		context.removeAttribute("dao");
	}

}
```



web.xml

```xml
<web-app>
	<listener>
		<listener-class>com.nts.todo.loader.InitListener</listener-class>
	</listener>
	<context-param>
		<param-name>jdbcDriver</param-name>
		<param-value>com.mysql.jdbc.Driver</param-value>
	</context-param>
</web-app>

```


