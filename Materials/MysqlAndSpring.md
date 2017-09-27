# MySql JDBC in a Spring Project

## Add this to your pom.xml file
````      
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<scope>runtime</scope>
</dependency>
````    
And click on "Import Changes" in the lower right corner

<img src="https://github.com/dat17v1/2_11_mysql_spring/blob/master/Materials/img/ImportChanges.png" width="300" />

## Add this to your application.properties file
````    
	spring.datasource.url=jdbc:mysql://localhost:3306/springbootdb
	spring.datasource.username=root
	spring.datasource.password=
	spring.jpa.hibernate.ddl-auto=create-drop
````    

## In your StudentController add a ````@Autowired```` anotation above the repository field

````    
    	@Autowired
    	IStudentRepository studentRepo = new StudentRepository();
````    

## In the Repository you should add a 

<pre>    
	<mark>@Repository</mark>
	public class StudentRepository implements IStudentRepository {
</pre>    
Above your class definition
and an attribute in the class.
````    
	@Autowired
	private JdbcTemplate jdbc;
````    

and use the different methods in that object to run the sql statements

### Insert
````    
	jdbc.execute("insert into user(name,email)values('Henning','clbo@jkea.dk')");
````     

### Update
````    
	jdbc
```` 

### Delete
````    
	jdbc
```` 


### Select
````    
	SqlRowSet users = jdbc.queryForRowSet("SELECT * FROM user");
        while (users.next()) {
           usersList.add(new User(users.getString("name"), users.getString("email")));
        }
```` 





