## Spring DAO 정리

- @Repository annotation 사용

- Spring JDBC가 JDBC를 편하게 하기 위해 제공하는 이미 구현된 객체

  - NamedParameterJdbcTemplate

    - JdbcTemplate은 바인딩 할때 ? 사용 

      ?를 사용하기 되면 sql문자열만 봤을때는 의미를 알기 힘들다. 

      ​	=> NamedParameterJdbcTemplate 사용

    - 이름을 이용해 바인딩하거나 결과값을 가져올 때 사용

    - query() / queryForObject() / update()

  - SimpleJdbcInsert 

- 생성자

  - 파라미터로 DataSource 객체를 받는다.
    - Spring ver4.3부터는 @ComponentScan으로 객체를 찾았을 때, 기본 생성자가 없다면 자동으로 객체를 주입해준다.
    - DBConfig에서 @Bean으로 등록했던 DataSource가 파라미터로 전달이 됨
    - 이 DataSource를 받아들여서 NamedParameterJdbceTemplate 객체를 생성하게 된다.

- 메소드 작성

  - jdbc.query(sql, paramMap, rowMapper) 에 파라미터를 넣어준다.

    - sql : 실제 쿼리문. static import를 이용해 불러온다

    - paramMap : 비어있는 Map객체 선언

      sql문에 바인딩 할 값이 있을 경우, 바인딩할 값을 전달할 목적으로 사용하는 객체

    - rowMapper : select 한건 한건의 결과를 DTO에 저장하는 목적으로 사용

      BeanPropertyRowMapper 객체를 이용해 column의 값을 자동으로 DTO에 담아주게 된다.

- 데이터 베이스의 컬럼명이랑 DTO의 필드명을 꼭 맞춰준다!!!! (DB: snake, java:camel)

```java
@Repository
public class RoleDao {
	private NamedParameterJdbcTemplate jdbc;
	private SimpleJdbcInsert insertAction;
	private RowMapper<Role> rowMapper = BeanPropertyRowMapper.newInstance(Role.class);

	public RoleDao(DataSource dataSource) {
		this.jdbc = new NamedParameterJdbcTemplate(dataSource);
		this.insertAction = new SimpleJdbcInsert(dataSource)
                .withTableName("role");
	}
	
	public List<Role> selectAll(){
		return jdbc.query(SELECT_ALL, Collections.emptyMap(), rowMapper);
	}

}
```

