
# DevOps Engineer's Daily Guide to Spring Boot: Key Concepts and Folder Structure

This guide aims to provide DevOps engineers with a comprehensive overview of the essential concepts and folder structure of Spring Boot, focusing on daily operations and best practices. 

# Topics Discussed
   
- Web Servers
- Tomcat 
- Java Build Tools
- Maven vs Gradle
- JAR file
- WAR file
- Commands Used For Creating JAR and WAR files
- MAVEN Project Folder Structure
- SERVER.XML File Configuration
- JKS Key Storage
- CATALINA.OUT
- Installation of Tomcat8 on EC2 
- Application Properties
# 

# 1) Web Server

A web server is a computer system that hosts websites and delivers web pages to users browsers upon request.


- Hosting Websites: The web server stores all the files, images, scripts, and data that make up a website.

- Handling Requests: When you type a website address into your browser and hit enter, your browser sends a request to the web server where that website is hosted.

- Serving Content: The web server processes the request and sends the appropriate web pages back to your browser. This process is often called "serving" the web pages.

- Using Protocols: Web servers use HTTP (HyperText Transfer Protocol) or HTTPS (HTTP Secure) to communicate with your browser, ensuring the data is transferred correctly and securely.

- Web server is like a librarian who fetches the right book (web page) from the library (server) when you ask for it (enter a URL).

# 2) Tomcat Web Server

- Apache Tomcat, often referred to simply as Tomcat, is an open-source implementation of the Java Servlet, JavaServer Pages (JSP), Java Expression Language (EL), and Java WebSocket technologies. It is developed and maintained by the Apache Software Foundation.

- Tomcat is a software that helps run Java applications on web servers. It’s particularly good at handling Java-based web applications.

 # Key Features

- Servlet Container
- JSP Support
- Websocket Support
- Extensibility
- Security

# Java Servlet

- It is a Java program that runs on a server. It is responsible for handling requests from web browsers and sends back responses.
- Example: When you submit a form on a website, a servlet might process the form data and return a web page with the results.

# JavaServer Pages (JSP):

- It allows you to create dynamically generated web pages using Java.
- Creates the structure and content of web pages, embedding Java code as needed.

# Java Expression Language (EL):

- A language used in JSP to simplify the access and manipulation of data.
- Makes it easier to access and display data without writing complex Java code.

# WebSocket Support:

- WebSocket support in Tomcat allows for real-time, full-duplex communication between a client (like a web browser) and a server. 
- This means that both the client and the server can send and receive messages at any time.

# 


# 3) Build Tools
- Building tools in Java involves creating applications, libraries, or frameworks that assist developers in the process of software development.

- These tools automate the process of compiling, packaging, and deploying applications. 

# MAVEN
  - It is a build automation tool primarily used for Java projects. 
  - Manages project builds, dependencies, and documentation.
  - Uses a standardized directory layout and a file called pom.xml (Project Object Model) to define project dependencies, plugins, and build configurations.
  - Automatically downloads and includes libraries (dependencies) your project needs from a central repository.
  - Extends functionality via plugins, like compiling code, running tests, and packaging applications.

- In simple terms: Think of Maven as a smart assistant that helps you compile your Java code, manage the libraries you need, and package your application neatly, all based on a simple, standardized configuration file.


# GRADLE
  - Gradle is another build automation tool, also used for Java projects.
  - Similar to Maven, but more flexible and powerful.
  - Uses a file called build.gradle for configuration, written in Groovy or Kotlin, which is more flexible and allows for custom scripting.
  - Also manages and downloads project dependencies automatically.
  - Supports plugins for additional functionality, and its flexibility makes it suitable for complex projects.

- In simple terms: Gradle is like Maven's more flexible cousin. It not only helps you compile, manage libraries, and package your code but also lets you customize almost everything with a more powerful scripting language.  
# 
# 4) Maven v/s Gradle  
# i) Configuration
- Maven uses XML configuration (pom.xml) and it is more declarative.
- Gradle uses Groovy or Kotlin DSL for configuration (build.gradle or build.gradle.kts) and it is more flexible.

# ii) Dependency Management
- Maven manages dependencies through a central repository (Maven Central) and their dependencies are declared in the "pom.xml" file.
- Gradle also manages dependencies from repositories like Maven Central and others and their dependencies are declared in the "build.gradle" file.

# iii) Build Performance
- Maven executes goals and phases sequentially. Slower for large projects due to its less efficient handling of tasks.
- Gradle utilizes incremental builds, only re-executing tasks that have changed. Faster for larger projects with many tasks.

# iv) Community and Ecosystem
- Maven had older and more mature with a larger repository of plugins and libraries. Strong community support and extensive documentation.	
- Gradle has newer community but rapidly growing in popularity. Modern features and better suited for multi-language projects.

# Use Case
- Maven: Best for standard Java projects that benefit from a structured, declarative approach with mature tooling and community support.

- Gradle: Ideal for complex and multi-language projects that require a flexible, scriptable build tool with modern performance features.
# pom.xml
    

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    </project>

# build.gradle
    
    plugins {
    	id 'java'
    }

	repositories {
    	mavenCentral()
    }

	dependencies {
     	testImplementation 'junit:junit:4.12'
    }
# 
# 5) JAR (Java Archive)     
- JAR files are primarily used for packaging Java classes, libraries, resources, and metadata into a single compressed file. They are used for standalone Java applications or libraries.

- Java classes, dependenices, config files, libraries are packaged into a single file for distribution, deployment and execution.

# Structure
    my-spring-boot-app.jar
    |-- BOOT-INF/
    |   |-- classes/
    |   |   |-- com/
    |   |   |   |-- example/
    |   |   |       |-- MySpringBootApplication.class
    |   |   |       |-- service/
    |   |   |           |-- MyService.class
    |   |   |-- application.properties
    |   |   |-- static/
    |   |       |-- index.html
    |   |-- lib/
    |       |-- spring-core-5.3.8.jar
    |       |-- spring-boot-starter-web-2.5.2.jar
    |       |-- mysql-connector-java-8.0.25.jar
    |-- META-INF/
    |   |-- MANIFEST.MF
    |-- org/
    |   |-- springframework/
    |       |-- boot/
    |           |-- loader/
    |               |-- JarLauncher.class
    |               |-- WarLauncher.class
    |-- application.properties

#  Root Directory
- Contains compiled classes (.class) of your java programs.
- Resources contains non-code resources required by the application, such as configuration files, images, and other data files.



# META-INF Directory
	i) MANIFEST.MF:
        - A special file that contains metadata about the JAR file.
		- It can specify the main class of the application, version information, and other configuration details.

	Example: 
		Manifest-Version: 1.0
		Main-Class: com.example.MainClass

# BOOT-INF Directory
- It has two directories namely /classes and /lib 
#  i) BOOT-INF/classes 
-  Contains the compiled classes (.class) and application.properties files.

                       BOOT-INF/classes/
						|-- com/
						|   |-- example/
						|       |-- MySpringBootApplication.class
						|       |-- service/
						|              |-- MyService.class
						|-- application.properties

#  ii) BOOT-INF/lib 
-  Contains the JAR files of all dependencies required by the application.	

                        BOOT-INF/lib/
						   |-- spring-core-5.3.8.jar
						   |-- spring-boot-starter-web-2.5.2.jar
						   |-- mysql-connector-java-8.0.25.jar
# 
# 6) WAR file (Web Application Archive)
- WAR files are specifically designed for packaging entire web applications in Java. They include not only Java classes and resources but also web-specific components such as HTML pages, JSP files, servlets, configuration files, and other web-related artifacts.

- Contains compiled Java classes, web pages (HTML, JSP), web-specific resources (CSS, JavaScript, images), servlets, configuration files (web.xml), and other web-related artifacts.

- By packaging the entire web application into a single file, WAR files simplify the deployment process. The WAR file can be deployed to any compatible web server such as Apache Tomcat, Jetty, etc or application server.

- The web.xml file holds configuration information for the web application, defining how servlets, filters, listeners, context parameters, welcome files, and error pages should be handled. This helps in managing the behavior and settings of the web application centrally.					

- Example: A WAR file for an e-commerce website containing all the necessary code and resources to run the application.

- Example: Deploying a WAR file to an Apache Tomcat server involves copying the WAR file to the server's webapps directory.

# Purpose
- To package web applications that can be deployed on a web server.
- Facilitates the distribution of web components and resources needed for running web applications.

# Structure 
        my-webapp.war                       								(war file)
			|-- index.html													(root directory)
			|-- styles.css                     								(root directory)
			|-- scripts.js      											(root directory)
			|-- login.jsp                      								(root directory)
			|-- images/ 													(root directory subdirectory)
			|     |-- logo.png       										(root directory subdirectory content)
			|-- WEB-INF/													(special directory within the root directory)
    				|-- web.xml
    				|-- classes/
    				|      |-- com/example/MyServlet.class
    				|      |-- config.properties
    				|-- lib/
        				  |-- my-library.jar
        				  |-- another-library.jar
# 
# Root Directory
- It contains static resources accessible to the client
- It includes static resources such as html files, css files, javascript files, images and media, etc.

# WEB-INF Directory
- Contains server-side resources and configuration files, not directly accessible by the client.
- This directory is protected and not accessible directly by clients for security reasons.	
# web.xml 
The web.xml file is a configuration file for a Java web application. It is located in the WEB-INF directory of a WAR file and defines various settings and components of the web application. It holds,
- Servlet definitions: define servlets and map them to specific URLs
-  Filter defn: define filters that can process requests and responses.
-  Listener Definitions: define event listeners for lifecycle events (like application startup and shutdown).
- Context Parameters: define global parameters accessible to the entire web application.
- Welcome Files: define default files that should be served when a directory is requested.
- Error Pages: define custom error pages for specific error codes or exceptions.                          
# 
# 7) Commands for Creating JAR and WAR with Maven
i) JAR file with MAVEN
    
    STEP 01: Create a Maven Project
    STEP 02: Navigate to the project (say my-app)
    STEP 03: Build jar using:
  		    # mvn clean package
    This generates a JAR file in the 'target' directory.. eg., target/my-app-1.0-SNAPSHOT.jar

ii) WAR file with MAVEN
    
    STEP 01: Create a Maven Project
  	STEP 02: Navigate to the project (say my-webapp)
  	STEP 03: Build war using:
  		    # mvn clean package
  	This generates a WAR file in the target directory, e.g., target/my-webapp.war
# 
# 8) Commands for Creating JAR and WAR with Gradle
i) JAR file with Gradle

    STEP 01: Create a Gradle Project:
    	# mkdir my-app
		# cd my-app
		# gradle init --type java-application

	STEP 02: Build jar 
		# gradle build
    This generates a JAR file in the build/libs directory, e.g., build/libs/my-app.jar

ii) WAR File   	

 	STEP 01: Create a gradle web project
 		# mkdir my-webapp
		# cd my-webapp
		# gradle init --type java-library

	STEP 02: Configure for WAR		
		Add the war plugin in build.gradle:

		plugins {
    		id 'java'
    		id 'war'
		}

		repositories {
    		mavenCentral()
		}

		dependencies {
    		implementation 'javax.servlet:javax.servlet-api:4.0.1'
    		testImplementation 'junit:junit:4.12'
		}
	
	STEP 03: Build war
		    # gradle build
	This generates a WAR file in the build/libs directory, e.g., build/libs/my-webapp.war
# 
# 8) MAVEN Folder Structure
        
        my-spring-boot-app/
        ├── src/
        │   ├── main/
        │   │   ├── java/
        │   │   │   └── com/
        │   │   │       └── example/
        │   │   │           └── myapp/
        │   │   │               ├── Application.java
        │   │   │               ├── controller/
        │   │   │               │   └── MyController.java
        │   │   │               ├── service/
        │   │   │               │   └── MyService.java
        │   │   │               ├── repository/
        │   │   │               │   └── MyRepository.java
        │   │   │               ├── model/
        │   │   │               │   └── MyModel.java
        │   │   │               └── config/
        │   │   │                   └── AppConfig.java
        │   │   ├── resources/
        │   │   │   ├── static/
        │   │   │   │   ├── css/
        │   │   │   │   │   └── styles.css
        │   │   │   │   ├── js/
        │   │   │   │   │   └── scripts.js
        │   │   │   │   └── images/
        │   │   │   │       └── logo.png
        │   │   │   ├── templates/
        │   │   │   │   └── index.html
        │   │   │   ├── application.properties
        │   │   │   ├── application.yml
        │   │   │   ├── messages.properties
        │   │   │   ├── logback-spring.xml
        │   │   │   └── data.sql
        │   │   └── webapp/
        │   │       └── WEB-INF/
        │   │           └── web.xml
        │   ├── test/
        │   │   └── java/
        │   │       └── com/
        │   │           └── example/
        │   │               └── myapp/
        │   │                   └── MyAppTests.java
        ├── .gitignore
        ├── mvnw
        ├── mvnw.cmd
        ├── pom.xml
        └── README.md
# 
# 9) server.xml
- The server.xml file is a configuration file used by Apache Tomcat, a popular Java Servlet Container.
- This file configures how Tomcat serves applications and handles requests.
- It contains : 
    
# i) Server Element
- It defines the entire server configuration. It s like a secret code word used to safely turn off the server.
- To turn off the server, connect to the port 8005 and type "SHUTDOWN".
- This element defines the overall config for the tomcat server instance.

          <Server port="8005" shutdown="SHUTDOWN">
          Commands to stop the tomcat server:
			    # telnet localhost 8005
			    # 'SHUTDOWN'

# ii) Service Element
- It is used to define a group of settings that control how Tomcat processes incoming requests for a specific service. 
- "Catalina" is just a name for this particular service group within Tomcat.
- Defines a collection of Connectors and an Engine. 
- Handles incoming requests.
			
            <Service name="Catalina">

# iii) Connector Element
- It defines how tomcat receives requests. It listens for client requests on a specific port.

			<Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />

# iv) Engine Element
- This part processes the incoming requests and determines how to handle them.

			<Engine name="Catalina" defaultHost="localhost">


# v) Host Element
- Defines a virtual host, which is a domain or subdomain.
			
            <Host name="localhost" appBase="webapps" unpackWARs="true" autoDeploy="true">

# vi) Context Element 
- It defines a web app that is to be ran within selected virtual host.

		 <Context path="" docBase="myapp" reloadable="true"/>
# 
# 10) JKS Keystore
- A JKS keystore is used to securely store cryptographic keys (like SSL/TLS keys) and their corresponding digital certificates.
-  It provides a way to manage and protect sensitive information such as private keys and certificates used for encryption, authentication, and integrity verification in Java applications.
- Encrypted private keys used for server-side authentication or data encryption.
- Digital certificates issued by Certificate Authorities (CAs) that authenticate the identity of servers or clients in secure communications.
- Public keys of trusted entities used to validate certificates presented by others.
- A JKS keystore is typically stored as a file (e.g., keystore.jks) on the file system.
- It ensures secure communication and authentication processes, crucial for maintaining the integrity and confidentiality of data exchanged over networks.

# i) Creation
- You can create a JKS keystore using Java's keytool utility, which comes with the JDK.

        keytool -genkeypair -alias mydomain -keyalg RSA -keystore keystore.jks -storepass password

# ii) Management
- Use keytool to manage entries (keys and certificates) within the keystore, including adding, removing, and listing entries.

        keytool -list -v -keystore keystore.jks -storepass password
# 
# 11) Installation Guide  
Installation for setting up Tomcat 8 on EC2 Instance.

- STEP 01: SSH into your EC2 instance

         ssh -i "akshay.pem" root@ec2-10-100-220-78.ap-south-1.compute.amazonaws.com  

- STEP 02: Download Apache Tomcat 8

         sudo wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.61/bin/apache-tomcat-8.5.61.tar.gz

- STEP 03: Extract the downloaded file

        sudo tar -xvzf apache-tomcat-8.5.61.tar.gz

- STEP 04: Rename the extracted folder for simplicity

        mv apache-tomcat-8.5.61 tomcat8

- STEP 05: Change to the Tomcat bin directory

        cd /tomcat8/bin

- STEP 06: Start Tomcat8

        ./startup.sh (OR) sh startup.sh

- STEP 07: Verify if Tomcat is running on port 8080 

        sudo lsof -i -P -n | grep LISTEN

- STEP 08: Open a web browser and navigate to

        http://your-ec2-public-ip:8080
# 
# 12) Application Properties
'application.properties' file is a configuration file used in Java-based applications (like those built with Spring Boot) to define settings and parameters. These settings can include things like:    

        Database connection details (URL, username, password)
        Server port numbers
        Application-specific properties
        Logging levels
        Email server settings      
By placing these configurations in application.properties, you can easily manage and change your application's behavior without altering the code.

## Documentation

[Apache Tomcat](https://tomcat.apache.org/)

[Youtube](https://www.youtube.com/watch?v=1bnla8eYcaI)







    


