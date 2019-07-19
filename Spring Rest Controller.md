## Spring Rest Controller

@RestController



- MessageConvertor

  외부에서 전달받은 제이슨 메서드를 내부에서 사용할 수 있는 객체로 변환

  컨트롤러를 리턴한 객체가 클라이언트에게 json으로 변환하여 전달할 수 있도록 역할

  @EnableWebMvc 로 하면 기본으로 제공

  

- jackson라이브러리

  json으로 변한하기 위해서 기본 MessageConvertor는 잭슨 사용

  근데 만약에 jakson 라이브러리가 제대로 추가 안되있으면 동작 안한다 (500에러)



- DispatcherServlet은 jsonMessageConvert를 내부적으로 사용해 Map객체를 json으로 변환하여 전송을 하게된다.

  => 클라이언트한테 응답이 갈때는 모두 json 형태로 변환되어 전송된다. 
