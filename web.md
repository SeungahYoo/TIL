

#### java의 특징

1. 객체지향언어 (OOP : Object Oriented Programing)

   하나의 기능을 객체로 만들어, 이러한 객체들을 결합해서 하나의 프로그램을 만든다.

2. 이식성이 높다. 종속적이지 않다. 보안성이 좋다.

   JVM(Java Virtual Machine)위에서 돌아가기 때문에, 운영체제 종류에 상관없이 돌아간다. 

3. 메모리를 자동으로 관리

   C언어의 경우 메모리를 직접 관리해줘야 하지만, java는 ==가비지 컬렉터(garbage collector)==에 의해 사용하지 않는 객체는 자동으로 메모리에서 제거한다. (컴퓨터에게 자원을 반납)

4. Multi-Thread 지원.

   (1) 동시에 여러가지 작업을 하는 경우

   (2) 대용량 작업을 빨리 처리할 경우

5. 동적로딩

   미리 객체를 만들지 않고, 필요한 시점에 동적으로 로딩해 객체를 생성할 수 있다.

   유지 보수시 특정 객체만 쉽게 수정 및 교체하여 사용이 가능하다.

6. 풍부한 오픈소스 라이브러리



#### 객체지향 언어의 특징

1. 추상화(Abstraction)

   객체들의 공통적인 특징(속성/기능)을 뽑아내는 것.

2. 캡슐화(Encapsulation)

   데이터 구조와 데이터를 다루는 방법을 결합시켜 묶는 것.

   데이터를 은닉하고, 그 데이터를 접근하는 기능을 노출시키지 않는의미로 사용되기도 한다. Private

3. 상속성

   상위개념의 특징을 하위개념이 물려받는 것

4. 다형성

   다른일을 하는 함수를 동일한 이름으로 호출



#### java 컴파일 과정

HelloWorld.java 

​			| 컴파일(javac.exe)

HelloWorld.class

​			| 실행(java.exe)

클래스 로더 : 클래스를 JVM으로 가져옴

​			|

Byte Code Verifier : Byte Code 검증

​			|

인터프리터 : Byte Code -> Binary code (JVM의 클래스 영역에 저장)

​			|

Runtime : 실행



#### 객체와 클래스의 차이

- 클래스(Class) : 현실 세계의 객체의 속성과 동작을 추려내 필드와 메소드로 정의한 것. 아직 메모리가 할당되지 않은 상태.
- 객체(Object) : class를 기반으로 실제 메모리에 할당된 상태.



#### 객체지향프로그래밍

클래스 기반으로 객체들을 조합해 전체 프로그램을 완성해 나가는 개발 기법.

- 캡슐화, 은닉화 : 외부 객체에서 구현방식은 알 수 없도록 숨기고 별도로 접근할 수 있는 getter/setter메서드를 통해 접근하는 방식.
- 상속 : 부모 class를 자식이 접근할 수 있도록 물려받는 방식
- 다형성 : 부모 클래스 타입으로 해당 부모를 상속받는 여러 자식 class를 대입할 수 있는 성질



#### java의 메모리 영역

- 메서드 영역 : static변수, 전역변수, 코드에서 사용되는 클래스 정보
- 스택 영역 : 지역변수, 함수등이 할당되는 LIFO 방식의 메모리
- 힙 : new 연산자를 통한 동작할당된 객체들이 저장된다. 가비지 컬렉터에 의해 메모리가 관리된다. 



#### 추상 메서드? 추상 클래스?

- 추상 메서드 : 메소드의 정의부만 있고 구현부는 있지않은 메소드
- 추상 클래스 : 추상 메소드를 적어도 하나 이상 가지고 있는 클래스로, 자식클래스에서 오버라이딩이 필요한 추상메소드를 가지고 있기 때문에 객체화 할 수 없다.



#### 인터페이스

모든 메소드가 추상메소드로 이루어진 클래스. Abstract 키워드를 붙이지 않아도 자동으로 모든 메소드가 추상메소드로 정의가 된다. 모든 변수가 자동으로 final static 키워드가 붙는다.

- 사용 이유

  개발코드에서 객체의 내부 구조를 모르더라도 인터페이스의 메소드명만 알고 있으면 된다. 해당 메소드를 통해 나오는 결과물을 알고 있기 때문에 다른팀의 작업을 기다리고 있지 않아도 된다.

  해당 객체가 수정될 경우 개발 코드 부분은 수정하지 안항도 된다.



#### Process vs Thread

- 프로세스

  OS가 메모리 등의 자원을 할당해준 실행중인 프로그램.

  각각의 프로세스는 서로 메모리 공간을 독자적으로 갖기 때문에 서로 메모리 공간을 공유하지 못한다. 공유하기 위해서는 IPC와 같은 방식이 필요하다.

- 쓰레드

  프로세스내에서 프로세스 자원을 가지고 CPU에 작업 요청을 하는 실행 단위

  각 쓰레드는 독자적인 stack 메모리를 갖고 그 외의 자원은 프로세스 내에서 공유한다.



#### Collection Framework

<img src="https://2.bp.blogspot.com/-DJT1edGbrPw/W2sqGwiALVI/AAAAAAAADEI/McUBmaGXswI_RHnDtpP-4HrkX7aVWe2PACLcBGAs/s1600/collections-framework-hierachy.gif"/>

- Interface
  - List : 배열과 유사. 추가할때마다 자동으로 boundary를 늘려주는 구조. 중복 데이터 허용. 순서 존재



#### Cookie / Session / Cache

- Stateless -> Stateful : 쿠키, 세션
- 쿠키
  - 브라우저에 의해 클라이언트 측에 저장. 
  - 서버는 특정 클라이언트가 무엇을 주문했는지 기억하지 않고 클라이언트가 저장되어 있는 데이터를 불러와 반복적으로 서버에 요청
  - 텍스트 형식으로 저장
  - 쿠키가 사라지는 시점은 쿠키를 저장할 때 설정, 설정하지 않으면 브라우저 종료시 삭제
  - 단점 : 사용자의 데이터가 컴퓨터에 저장된다는 점. —> 보안 이슈
- 세션
  - 서버측에 저장
  - 특정 클라이어트가 무엇을 요청하는지 저장되어 있어 요청에 대한 응답을 실행

- 캐시
  - 웹페이지 리소스(오디오, 비디오, 이미지 등)의 임시 저장소
  - 다음에 같은 웹페이지 접속시 페이지 로딩 속도를 개선해주는 역할



#### Request 전송 방식

- GET : URL의 쿼리문자열에 데이터를 같이 전달하는 방식. 데이터 길이 제한, 보안에 취약
- POST : 헤더에 데이터를 넣어 보냄. 보안에 조금더 유리. 데이터 길이제한x. get에 비해 느림
- DELETE : restful에서 삭제기능
- PUT/PUSH : restful에서 수정



#### RESTful이란

- 리소스와 행위를 명시적이고 직관적으로 분리한다.
- 리소스는 URI로 표현, 리소스가 가리키는 것은 명사로 표현
- 행위는 HTTP Method로 표현하고, GET(조회), POST(생성), PUT(수정), DELETE(삭제)를 분명한 목적으로 사용.

REST란 웹에 존재하는 모든 자원에 고유한 URI를 부여해 활용하는 것. 자원을 정의하고 자원에 대한 주소를 지정하는 방법론.

RESTful API는 REST 특징을 지키면서 API를 제공하는 것을 의미.

- REST 개념이 대두된 이유

  '애플리케이션 분리 및 통합', '다양한 클라이언트의 등장'



#### Spring DI

DI는 Dependency Injection(의존성 주입)의 약자로, 객체들 간의 의존성을 줄이기 위해 사용되는 Spring의 IOC 컨테이너의 구체적인 구현 방식.

객체 자체가 아니라 Framework에 의해 객체의 의존성이 주입되는 설계 패턴



일반적으로 class를 사용하기 위해서는 instance 생성을 해야한다.

그런데 instance 생성 비용이 크다거나, 여러군데서 사용한다거나, 하는 경우에는 비효율적이다. 이럴때 instance의 생성을 컨테이너(spring framework)에 맡겨서 일괄적으로 진행한 후 life-cycle 관리 역시 컨테이너에 맡기는 것.

내가 필요할때에 @autowired, @inject등으로 instance를 컨테이너로부터 주입받아 사용.

instance의 생성 및 관리 주체가 컨테이너가 되기 때문에 Inversion Of Controls, 제어의 역전.

장점 

	- 종속성 감소 -> 변경에 민감하지 않다.
	- 재사용성 증가
	- 더 많은 테스트코드를 만들 수 있다.
	- 코드를 읽기 쉬워진다.



#### MVC Pattern

- model : data 처리와 접근 - 데이터베이스 관리

- View : client에 보여지는 화면을 담당

- controller : model과 view를 제어

  데이터와 화면간의 의존관계를 벗어날수 있게 하는 개발기법. 



#### MVC 구조 흐름

1. 디스패처 서블릿이 클라이언트로부터 요청을 받으면, 이를 요청할 핸들러 이름을 알기 위해 핸들러맵핑에게 물어본다.
2. 핸들러맵핑은 요청 url을 보고



#### 오버로딩 vs 오버라이딩

- 오버로딩 : 메서드명은 동일하지만, 매개변수 타입과 개수를 다르게 선언하는 방식
- 오버라이딩 : 상속한 자식에서 부모의 메서드를 재정의하는 방식.



#### Wrapper class

기본형타입(int, double, char, boolean ..)을 객체로 사용해야 하는 경우 사용되는 클래스.

java에는 각 기초 타입에 대해 JAVA클래스 라이브러리 내에 상응되는 wrapper class가 존재한다!

Boxing : 기본 자료형 -> Wrapper 객체

unboxing : wrapper객체 -> 기본자료형
Jdk 1.5버전 이후에는 autoBoxing, autoUnboxing 지원.

- 사용이유 : 기본 data타입은 객체가 아니어서 object로 받는 다형성을 지원할 수 없다. 하지만, 메소드에서 실제로 기본데이터 타입을 다형성



#### RDB vs noSQL

- RDB(Relational Database)
  - 테이블마다 스키마를 정의해야된다.
  - 데이터의 정확성을 보장한다.
  - SQL 질의문을 통해 요청 처리
- NoSQL(Not only SQL)
  - mongoDB, hBase
  - RDB의 확장성 이슈를 해결하기 위해 나온 DB 모델
  - 비교적 저렴한 가격으로 DB성능을 높일 수 없다.
  - 여러 개의 테이블이 아닌, 큰 테이블 하나만을 사용한다.
  - key-value 방식 
  - SQL사용 안함
  - Schema-less : 구조 변경 용이 / 데이터 형식 다양/ 바꾸기 쉽다/ 정확석<데이터 양



#### DB Index

RDBMS에서 검색속도를 높이기 사용하는 하나의 기술

TABLE의 컬럼을 색인화(따로 파일로 저장)하여 검색시 해당 TABLE의 레코드를 full scan하는게 아니라 색인화 되어있는 Index파일을 검색하여 검색속도를 빠르게 한다.

- 트리구조
- 장점
  - 테이블에서 검색과 정렬속도 향상
  - 테이블 행의 고유성 강화
  - 테이블의 기본 키는 자동으로 인덱스 된다.
- 단점
  - 여러 사용자가 한 페이지를 동시에 수정할 수 있는 병행성이 줄어든다.
  - 인덱스 된 필드에서 데이터를 업데이트하거나, 레코드를 추가/삭제 할때 성능 떨어짐
  - 인덱스가 db공간을 차지해 추가적인 공간이 필요하다
  - 인덱스 생성하는데 시간이 많이 소요될 수 잇다.
  - 데이터 변경 작업이 자주 일어나면 인덱스를 재작성해야할 필요가 있다.



#### Spring vs SpringBoot

스프링 부트는 스프링에서 사용하는 프로젝트를 간편하게 셋업할 수 있는 서브 프로젝트.

독립 컨테이너에서 동작할 수 있기 때문에 임베디드 톰켓 자동 실행.

임베디드 컨테이너에서 애플리케이션을 실행시키기에는 다소 불안전해서 큰 프로젝트를 사용하지 않는 것이 좋다.



#### Spring Bean

POJO(Plain, old java object) = 'Beans'

Beans는 애플리케이션의 핵심을 이루는 객체이며, Spring IoC(Inversion of Control)컨테이너에 의해 인스턴스화, 관리, 생성된다.

Beans는 우리가 컨테이너에 공급하는 설정메타데이터(XML파일)에 의해 생성된다.

​	- 컨테이너는 이 메타데이터를 통해 Bean의 생성, Bean Life Cycle, Bean Dependency 등을 알 수 있다.



- Spring Bean Scope
  - 스프링은 기본적으로 모든 bean을 singleton으로 생성하여 관리한다.
  - 

#### Spring AOP?

로그인 - advice

글쓰기 전, 판매 전, <- 조인포인트 : 끼어들어갈수 있는 포인트

조인포인트의 시점들. 조인포인트를 묶은게 포인트 컷.



AOP : 관점지향프로그래밍의 약자로 핵심업무에서 중복적으로 공통업무를 해결하기 위해 나온 방식.

에스팩트 = 어드바이스 + 포인트컷. 


