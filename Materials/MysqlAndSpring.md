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

## In your UserController add a ````@Autowired```` anotation above the repository field

````    
    	@Autowired
    	IUserRepository userRepository = new UserRepository();

````    
## Create a UserRepository that implements the IUserRepository interface
### In the Repository you should add a 
<pre>    
	<b>@Repository</b>
	public class StudentRepository implements IStudentRepository {
</pre>    
Above your class definition
and two attributes in the class.
````    
	@Autowired
	private JdbcTemplate jdbc;
````    

The jdbc object has diffent methods you will use for querering the database.

Use the different methods in that object to run the sql statements

### Insert
````    
	jdbc.update("INSERT INTO user (name, email) VALUES ('"+ user.getName() + "','" + user.getEmail() + "')");
````     

### Update
````    
	jdbc.update("UPDATE user SET " +
                "name ='"+ user.getName() +"' , " +
                "email='"+ user.getemail() +"' WHERE user_id = '"+ user.getUserId() +"'");
```` 

### Delete
````    
	jdbc.update("DELETE FROM user WHERE user_id='" + id + "'");
```` 


### Select (all)
````    
	SqlRowSet users = jdbc.queryForRowSet("SELECT * FROM user");
        while (users.next()) {
           usersList.add(new User(users.getString("name"), users.getString("email")));
        }
````     

### Select (one)
````    
	
	SqlRowSet user = jdbc.queryForRowSet("SELECT * FROM students where student_id ='" + id + "'");
        while (user.next()) {
           return new User(user.getInt("user_id"),user.getString("name"), user.getString("email")));
        }

````    





