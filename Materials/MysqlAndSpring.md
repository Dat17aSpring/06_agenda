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

## In your StudentController add ```` @Autowired  ```` above the repository field

````    
    @Autowired
    IStudentRepository studentRepo = new StudentRepository();
````    




