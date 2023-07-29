# Connect Java code from database using Hibernate and JDBC 
Know how to connect java code from database using JDBC and Hibernate in simple steps


Connecting Database from java using a Hibernate framework of java with maven. 
<br>
Step 1. Add two dependencies (First one is of hibernate and second is MySQL connector) in POM.XML file with in Dependencies tag.
<!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-core -->
		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>5.5.4.Final</version>
		</dependency>
<!-- https://mvnrepository.com/artifact/com.mysql/mysql-connector-j -->
		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<version>8.0.33</version>
		</dependency>
Step 2. Create hibernate.cfg.xml file in “src/main/java”  and add this code

	<?xml version="1.0" encoding="UTF-8"?>
	<!DOCTYPE hibernate-configuration PUBLIC
	"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
	"http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
	<hibernate-configuration>
	<session-factory>
		<!-- MySQL database driver class -->
		<property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver
		</property>
		<!-- MySQL database connection URL -->
		<property name="hibernate.connection.url">jdbc:mysql://localhost:3306/DB_name?serverTimezone=UTC</property>
		<!-- MySQL database username -->
		<property name="hibernate.connection.username"> username </property>
		<!-- MySQL database password -->
		<property name="hibernate.connection.password"> password </property>
		<!-- Dialect for MySQL -->
		<property name="hibernate.dialect">org.hibernate.dialect.MySQL5Dialect</property>
		<!-- Update the database schema automatically -->
		<property name="hibernate.hbm2ddl.auto">update</property>
		<!-- Show SQL statements in the console -->
		<property name="hibernate.show_sql">true/false</property>
		<!-- Mapping configuration for the BankUser class -->
		<mapping class="PATH OF Entity File"></mapping>
	</session-factory>
	</hibernate-configuration>

Step 3. Create java file in main package and then 

		// 1.Create a Hibernate SessionFactory
		SessionFactory factory = new Configuration().configure("hibernate.cfg.xml").buildSessionFactory();
		// 2.Open a new session
		Session session = factory.openSession(); 
		// To save the object we need to create the object first
		// Creating object of name
		ClassName ObjectName = new ClassName ();
		ObjectName. Setter(Argument);
		ObjectName.Setter(Argument);
		// Beginging the transaction to save this object in DB
		Transaction tx = session.beginTransaction();
		// Saving the object by passing the object name
		session.save(ObjectName);
		// commiting the transaction
		tx.commit();
		// To get the data from DB 
		ClassName Variable = session.get(ClassName.class, ID);
		// Printing the data from DB
		System.out.println(Variable.Getter()+" "+ Variable.Getter());
		// 3.Finally, close the session
		session.close();
		System.out.println("Succesfully executed");
		// 4.Close the Hibernate SessionFactory 
		factory.close();
  
Connecting Database from java using JDBC (Java API) maven
<br>
Step 1. Add MySQL-connector-j dependency in POM.XML file.

	<dependencies>
		<!-- https://mvnrepository.com/artifact/com.mysql/mysql-connector-j -->
		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<version>8.0.33</version>
		</dependency>
	</dependencies>
 
Step 2. Establish a connection

	// 1.Establish Connection 
	Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/bank","UserName", "Password");
	// 2.create a statement
	Statement stmt = con.createStatement();
	// 3.Write the query
	String s = "INSERT INTO user(First_Name) VALUES('" + Fname + "')";
	// 4.Execute statement it will save run the query in  the DB
	stmt.execute(s);
	// 5. To get all data
	String all = "SELECT * FROM TableName";
	// 6. store data in result set
	ResultSet rs = stmt.executeQuery(id);
	while (rs.next()) {
		int User_id = rs.getInt("Respective_Column_name");
		String Fname1 = rs.getString("Respective_Column_name");
		System.out.println( id+" "+ Fname1);
		}
	// 7. Closing the connection
	con.close();



# ***🌟Give Star If you find this helpful and thank you :)🌟***


