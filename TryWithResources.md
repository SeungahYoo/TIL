## Try with resources

JDK1.7 에는 AutoCloseable 인터페이스가 추가됐다.

```java
/**
 * @author Josh Bloch
 * @since 1.7
 */
public interface AutoCloseable {
    void close() throws Exception;
}
```



인터페이스 추가와 함께 try절에 ()가 들어갈 수 있게 됐다.

```java
public static void main(String[] args) {
    try(FileInputStream fis = new FileInputStream("")){
         
    }catch(IOException e){

    }
}

```

이런식으로 try(){} 형태로 사용이 가능하며 ()안에 들어올 수 있는건 AutoCloseable 구현체 뿐이다.

이런 문법을 <b>try with resources</b> 라고 부른다.



장점은 다음과 같다.

- try catch 절이 종료되면서 자동으로 close() 메서드를 호출해준다.
- 코드의 길이를 현저히 줄이면서 가독성을 높인다.



try() 구문 안에서 자원을 생성하면, 알아서 `close()` 를 호출해준다.
