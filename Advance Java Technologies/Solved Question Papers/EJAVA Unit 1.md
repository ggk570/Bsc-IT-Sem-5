#### <span style="color:blue;">1. What are different technologies provided by Java EE platform.</span>
1. Java EE is actually a collection of technologies and APIs for the Java platform designed to support "Enterprise" Applications which can generally be classed as large-scale, distributed, transactional and highly-available applications designed to support mission-critical business requirements. Java EE is now known as Jakarta EE.
2. Java EE (Enterprise Edition), now known as Jakarta EE, provides a robust set of technologies for developing enterprise-level applications. Some of the Key Technologies included in Java EE are:
	1. **Java Servlets:** Enable server-side Java code to handle requests and responses, forming the backbone of web applications.
	2. **JavaServer Pages:** Allows the embedding of Java code in HTML pages, making it easier to create dynamic web content.
	3. **JavaServer Faces:** A component-based web framework for building user interfaces for web applications.
	4. **Enterprise JavaBeans (EJB):** It is a server-side component that encapsulates the business logic of an application. The business logic is the code that fulfills the purpose of the application.
	5. **Java Persistence API (JPA):** It is a framework for object-relational mapping (ORM) in Java. It's used to map Java objects to tables in a relational database.
	6. **Context Dependency Injection (CDI):** Provides a set of services to manage the lifecycle of components and their dependencies, promoting loose coupling and better architecture.
	7. **Java Message Service (JMS):** A messaging standard that allows applications to create, send, receive, and read messages, enabling asynchronous communication.
	8. **Java Transaction API (JTA):** It is an api to manage transactions in Java. It facilitates distributed transactions, ensuring data integrity across multiple resources.
	9. **Java Naming and Directory Interface (JNDI):** It provides naming and directory functionality to applications written in the Java programming language. JNDI is also defined independent of any specific naming or directory service implementation. It enables applications to access different, possibly multiple, naming and directory services using a common API. Using JNDI, applications based on Java technology can store and retrieve named Java objects of any type. In addition, JNDI provides methods for performing standard directory operations, such as associating attributes with objects and searching for objects using their attributes.
	10. **JavaMail API:** The JavaMail API provides a platform-independent and protocol-independent framework to build mail and messaging applications.
	11. **Java Web Services:** Supports the creation of SOAP and RESTful web services, allowing different applications to communicate over the web.
	12. **Security:** Java EE provides various security features including JAAS (Java Authentication and Authorization Service) for authentication and role-based access control.
	13. **WebSocket API:** Facilitates two-way communication between client and server over a single, long-lived connection.
	14. **JSON Processing (JSON-P) and JSON Binding (JSON-B):** These are APIs for processing JSON data and binding it to Java objects, respectively.

#### <span style="color:blue;">2. Explain 2 tier System Architecture, its advantage and disadvantage.</span>
1. A **2-tier architecture** is a client-server architecture where the user interface (client) and the database (server) are separated into two distinct layers.
2. In this model, the client directly communicates with the database server.
3. With two-tier client/server architectures, the user system interface is usually located in the user’s desktop environment and the database management services are usually in a server that is a more powerful machine that services many clients.
4. Advantages of 2 tier System Architecture:
	1. The architecture is straightforward, making it easier to develop and manage.
	2. Direct communication between the client and the database can lead to faster data access and processing since there’s no middle layer.
	3. Typically requires less hardware and software resources than more complex architectures, making it more affordable for smaller applications.
	4. Since the application is less complex, it can be easier to deploy and update client applications.
5. Disadvantages of 2 tier System Architecture:
	1. As the number of clients increases, performance can degrade since all clients directly connect to the database, potentially overloading it.
	2. It may lack advanced features like load balancing and failover mechanisms, which are more easily implemented in multi-tier architectures.
	3. Direct access to the database from the client can expose the database to security vulnerabilities, making it more challenging to secure sensitive data.
	4. Managing changes in the database structure may require changes in all client applications, leading to increased maintenance overhead.

#### <span style="color:blue;">3. Explain life cycle of servlet with a diagram.</span>
![[servlet life cycle.png]]
1. A **Servlet** in Java is a server-side component that handles client requests and generates dynamic web content.
2. It is a Java class that runs on a web server and is part of the Java EE (Enterprise Edition) specification.
3. A servlet goes through a series of stages called as lifecycle, these stages govern how a servlet is created, initialized, processed, and destroyed within a servlet container (like Apache Tomcat). The lifecycle of servlet is managed by Servlet Container. 
4. Below is a detailed explanation of each phase:
	1. **Loading:** The first stage of the Servlet lifecycle involves loading the Servlet by the Servlet container. The servlet container loads the servlet class when it receives a request for the servlet or at startup, depending on the configuration (e.g., `load-on-startup`). In this stage an instance of servlet is created by servlet container using no argument constructor.
	2. **Initializing:** After the Servlet is instantiated successfully, the Servlet container initializes the instantiated Servlet object. The container initializes the Servlet object by invoking the **Servlet.init(ServletConfig)** method which accepts ServletConfig object reference as parameter. The Servlet container invokes the **Servlet.init(ServletConfig)** method only once. This method is used to initialize the resources, such as JDBC datasource. Now, if the Servlet fails to initialize, then it informs the Servlet container by throwing the **ServletException** or **UnavailableException**.
	3. **Request Handling:** In this stage, the servlet is now ready to serve client requests. The servlet creates the **ServletRequest** and **ServletResponse** objects. In this case, if this is a HTTP request, then the Web container creates **HttpServletRequest** and **HttpServletResponse** objects which are subtypes of the **ServletRequest** and **ServletResponse** objects respectively. After creating the request and response objects it invokes the Servlet.service(ServletRequest, ServletResponse) method by passing the request and response objects. The **service()** method while processing the request may throw the **ServletException** or **UnavailableException** or **IOException**. Depending on the HTTP request method (GET, POST, etc.), the container calls the appropriate method.
	4. **Destruction:** When the servlet is no longer needed (e.g., the server is shutting down or the servlet is being removed), the servlet container calls the `destroy()` method. This method is used for cleanup tasks which includes Releasing Resources (e.g closing db connection), saving state if necessary. This method is also called only once.

#### <span style="color:blue;">4. What is JDBC? Explain JDBC architecure.</span>
1. ***JDBC*** stands for **Java Database Connectivity. JDBC** is a Java API to connect and execute the query with the database.
2. It provides methods for querying and updating data in a database, allowing developers to execute SQL statements, retrieve results, and manage database connections.
3. JDBC provides a common interface for accessing different types of databases.
4. It allows execution of SQL statements, including SELECT, INSERT, UPDATE, DELETE, and more.
5. JDBC manages connections to the database, allowing for efficient transaction control and resource management.
6. JDBC supports retrieval of results in various formats, making it versatile for different application needs.
**Architecture of JDBC:**
![[Architecture of JDBC.jpg]]
1. **Application:** It is a java applet or a servlet that communicates with a data source.
2. **JDBC API:** This layer includes classes and interfaces that Java developers use to connect to a database, send SQL statements, and process results. A few of the crucial interfaces and classes defined in the JDBC API are the following:
- Driver Interface
- Connection Interface
- DriverManager Class
- Statement Interface
- PreparedStatement Interface
- CallableStatement Interface
- ResultSet Interface
- ResultSetMetaData Interface
- DatabaseMetaData Interface
- RowSet Interface
- Blob Class
3. **JDBC Driver Manager:** It plays an important role in the JDBC architecture. It uses some database-specific drivers to effectively connect enterprise applications to databases.
4. **JDBC Drivers:** To communicate with a data source through JDBC, you need a JDBC driver that intelligently communicates with the respective data source.

#### <span style="color:blue;">5. Write short note on JDBC drivers.</span>
1. JDBC drivers are essential for connecting Java applications to databases. They translate Java calls to database-specific calls.
2. **JDBC drivers** are the software components which implements interfaces in JDBC APIs to enable java application to interact with the database.
3. There are four main types of JDBC drivers:
- **Type 1: JDBC-ODBC Bridge Driver** - Translates JDBC calls into ODBC (Open Database Connectivity) calls. It acts as a bridge between JDBC and ODBC drivers. It is also called Universal driver because it can be used to connect to any of the databases.
	Advantages:
	1. It is a database independent driver.
	Disadvantages:
	1. Mostly deprecated and not recommended for production use.
	2. Requires ODBC driver to be installed on the client machine.
	3. Performance overhead due to the bridge layer.
- **Type 2: Native API Driver** - It converts JDBC calls into database-specific native calls using the client library of the database. In order to interact with different database, this driver needs their local API, that’s why data transfer is much more secure as compared to type-1 driver. This driver is not fully written in Java that is why it is also called Partially Java driver.
	Advantages:
	1. Better performance than Type 1 because it uses native code.
	2. More efficient for complex operations compared to Type 1.
	Disadvantages:
	1. Requires native database client libraries to be installed on the client machine.
	2. Not portable, as it depends on the specific database client.
	3. It is a database dependent driver.
- **Type 3: Network Protocol Driver** - The Network Protocol driver uses middleware (application server) that converts JDBC calls indirectly into the vendor-specific database protocol. It works by converting JDBC calls into a database-independent protocol, which is then converted into database-specific calls by a server component.
	Advantages:
	1. Type-3 drivers are fully written in Java, hence they are portable drivers.
	2. Switch facility to switch over from one database to another database.
	Disadvantages:
	1. Network support is required on client machine.
	2. Maintenance of Network Protocol driver becomes costly because it requires database-specific coding to be done in the middle tier.
- **Type 4: Thin Driver** - A pure Java driver that converts JDBC calls directly into the database-specific protocol.
	Advantages:
	1. Does not require any native library and Middleware server, so no client-side or server-side installation.
	2. It is fully written in Java language, hence they are portable drivers.
	3. Since it is fully written is java it is platform independent.
	4. Typically the fastest among the four types due to direct communication.
	Disadvantages:
	1. Each database requires a separate driver implementation.
	2. Developers must manage the driver's updates and compatibility.

#### <span style="color:blue;">6. Write a program to accept details of a person and using servlet store those data in database.</span>
**index.html**
```
<!DOCTYPE html>
<html>
    <head>
        <title>Test</title>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    </head>
    <body>
        <form action="SaveServlet" method="post">
            <label for="name">Name: </label>
            <input type="text" id="name_input" name="name" required>
            <br>
            <label for="email">Email: </label>
            <input type="email" id="email_input" name="email" required>
            <br>
            <input type="submit" value="Submit">
        </form>
    </body>
</html>
```
**SaveServlet.java**
```
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

public class SaveServlet extends HttpServlet {

    private static final String DB_URL = "jdbc:mariadb://localhost:3306/Test1";
    private static final String DB_USER = "root";
    private static final String DB_PASS = "";
    
    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            out.println("<!DOCTYPE html>");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Save Servlet</title>");
            out.println("</head>");
            out.println("<body>");
            
            String name = request.getParameter("name");
            String email = request.getParameter("email");
            try{
                Class.forName("org.mariadb.jdbc.Driver");
                Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASS);
                String insertQuery = "INSERT INTO persons (name, email) VALUES (?, ?)";
                PreparedStatement stmt = conn.prepareStatement(insertQuery);
                stmt.setString(1, name);
                stmt.setString(2, email);
                stmt.executeUpdate();
                out.println("<h1>Person's details are saved</h1>");
            }
            catch(Exception e){
                e.printStackTrace();
                out.println(e.getMessage());
            }
            
            out.println("</body>");
            out.println("</html>");
        }
    }

    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}
```
Add below line in dependencies in pom.xml
```
<dependency>
    <groupId>org.mariadb.jdbc</groupId>
    <artifactId>mariadb-java-client</artifactId>
    <version>3.4.1</version>
</dependency>
```

#### <span style="color:blue;">7. What is an enterprise application? What is enterprise edition of Java.</span>
**Enterprise Application:**
1. An **enterprise application** is a large-scale software solution designed to operate in a corporate environment
2. These applications are typically complex, distributed, and designed to handle a significant amount of data and user interactions.
3. Enterprise applications are designed in such a way to support various enterprise/corporate tasks such as customer relationship management, accounting etc.
4. These applications should have below features to work efficiently:
	1. **Scalability:** Enterprise applications should be scalable i.e they should be able to handle increase demand of clients.
	2. **Reliability:** These applications should be fault-tolerant and maintain high availability.
	3. **Integration:** They should be able to integrate with other systems, such as databases, external systems and legacy systems.
	4. **Security:** They should incorporate robust security measures to protect sensitive data and ensure compliance with regulations.
	5. **Performance:** They should be optimized for high performance to handle multiple transactions and users simultaneously.
	6. **Manageability:** They should include tools for monitoring, logging, and managing application health.
5. Examples: Customer Relationship Manager (CRM) systems, Enterprise Resource Planning (ERP) systems, Supply Chain Management (SCM) systems, Human Resource Management (HRM) systems.
**Enterprise Edition of Java**
1. **Java Enterprise Edition** which was earlier known as J2EE and is currently known as Jakarta EE.
2. It is a set of specifications wrapping around Java SE (Standard Edition).
3. The Java EE provides a platform for developers to develop applications with enterprise features such as distributed computing, security and web services etc.
4. Java EE includes a set of technologies and apis to support enterprise application development, these specifications include:
	1. **Web Specifications:**
	- Servlet: This specification defines how you can manage HTTP requests either in a synchronous or asynchronous way. It is low level, and other specifications depend on it
	- WebSocket: WebSocket is a computer communication protocol, and this API provides a set of APIs to facilitate WebSocket connections.
	- Java Server Faces:  It is a service which helps in building GUI out of components.
	2. **Web Service Specifications:**
	- Java API for RESTful Web Services: It helps in providing services having Representational State Transfer schema.
	- Java API for JSON Processing: It is a set of specifications to manage the information provided in JSON format.
	- Java API for JSON Binding: It is a set of specifications provide for binding or parsing a JSON file into Java classes.
	- Java Architecture for XML Binding: It allows binding of xml into Java objects.
	- Java API for XML Web Services: SOAP is an xml based protocol to access web services over http. This API allows you to create SOAP web services.
	3. **Enterprise Specifications of Java EE:**
	- Context Dependency Injection: CDI provides a common mechanism to inject component such as Enterprise JavaBeans (EJBs) or managed beans into other components such as JavaServer Pages (JSPs)
	- Enterprise Java Beans: EJB is a server-side software element that summarizes business logic of an application.
	- Java Persistence API: These are the specifications of object-relational mapping between relational database tables and Java classes.
	- Java Transaction API: It contains the interfaces and annotations to establish interaction between transaction support offered by Java EE.
	- Java Message Service: It provides a common way to Java program to create, send and read enterprise messaging system's messages.

#### <span style="color:blue;">8. Write a short note on javax.Servlet package.</span>
1. The `javax.servlet` package is a fundamental part of Java EE (now Jakarta EE) that provides the core interfaces and classes for developing server-side components known as servlets.
2. Servlets are Java programs that run on a server and handle requests and responses in web applications.
3. Some interfaces and classes in javax.servlet package:
	1. **Servlet:** The primary interface that must be implemented by all servlets. It defines the essential lifecycle methods, such as `init()`, `service()`, and `destroy()`.
	2. **ServletRequest:** Represents the request from a client. It provides methods to access request parameters, headers, and attributes.
	3. **ServletResponse:** Represents the response to be sent to a client. It allows the servlet to set response content type, headers, and output data.
	4. **ServletConfig:** Provides configuration information to the servlet, such as initialization parameters defined in the deployment descriptor (web.xml).
	5. **ServletContext:** Represents the web application environment and allows servlets to communicate with the servlet container. It provides methods to access application-wide parameters and resources.
	6. **GenericServlet:** An abstract class that implements the `Servlet` interface and provides basic functionality for servlets. Developers can extend this class to create servlets without dealing with HTTP specifics.

#### <span style="color:blue;">9. What is a jdbc statement ? Explain it's 3 types.</span>
1. In Java Database Connectivity (JDBC), a **Statement** object is used to execute SQL queries against a database.
2. It provides methods to send SQL commands to the database and retrieve results.
3. The Statement object is created from a `Connection` object and is essential for interacting with the database.
4. Types of JDBC Statements Object:
	1. **Statement:** Used for executing simple SQL queries without parameters. It is created using the `createStatement()` method of the `Connection` interface. This type is less efficient for executing the same query multiple times, as it doesn't support caching of compiled SQL.
	2. **PreparedStatement:** Used for executing precompiled SQL queries with or without input parameters. It is secure as it provides prevention against sql injection attacks. It is more efficient for executing the same SQL statement multiple times. It is created using the `prepareStatement(String sql)` method of the `Connection` interface.
	3. **CallableStatement:** Used to execute stored procedures in the database. It can also accept input and output parameters. It is created using the `prepareCall(String sql)` method of the `Connection` interface.

#### <span style="color:blue;">10. List and explain the tasks that Servlet can do.</span>
1. Servlets are java classes that handle requests and responses in web applications.
2. Servlets are managed by servlet containers on web server, servlet containers manage the complete life cycle of servlets.
3. Servlets performs some key tasks in Java enterprise applications, these tasks includes:
	1. **Processing client requests:** Servlets can process different types of HTTP requests, such as GET, POST, PUT, DELETE, etc. This allows them to handle various operations based on the client's request type. Servlets can retrieve and process parameters sent by the client in forms, query strings, or HTTP headers. This enables dynamic response generation based on user input.
	2. **Generating Dynamic Content:** Servlets can generate HTML, XML, or JSON content dynamically based on server-side processing, allowing for interactive web applications. They can incorporate business logic to produce dynamic content, such as fetching data from a database, performing calculations, or interacting with other services.
	3. **Session Management:** Servlets can manage user sessions by tracking session data across multiple requests. This is crucial for maintaining user state, such as login sessions and shopping carts.
	4. **Interacting with Database:** Servlets can connect to databases using JDBC (Java Database Connectivity) to perform CRUD (Create, Read, Update, Delete) operations. This is essential for applications that require data persistence.
	5. **Forwarding and Redirecting Requests:** Servlets can forward requests to other resources (e.g., another servlet, JSP, or HTML file) on the server using the `RequestDispatcher`. This allows for modular application design. They can send redirects to the client, instructing the browser to request a different URL. This is useful for implementing navigation or after-processing steps.
	6. **Handling Exceptions:** Servlets can handle exceptions that occur during request processing, providing meaningful error messages or redirecting users to error pages. They can specify custom error pages for various HTTP error codes (like 404 or 500) to enhance user experience.
	7. **Security Features:** Servlets can integrate with security frameworks to manage user authentication and authorization, ensuring that sensitive resources are protected. They can handle secure connections using HTTPS, ensuring data transmitted between the client and server is encrypted.
	8. **Asynchronous Processing:** Servlets can handle asynchronous processing, allowing them to manage long-running tasks without blocking the server. This improves the scalability of the application.

#### <span style="color:blue;">11. What are the challenges of enterprise application development.</span>
1. Enterprise application development comes with its own set of challenges due to the complexity, scale, and critical nature of these systems.
2. Here are some key challenges developers often face:
	1. **Complexity Requirements:** Enterprise applications must address varied business requirements from different departments or stakeholders, often leading to complex functionalities. Also Business needs can evolve, necessitating changes to the application during the development process.
	2. **Integration with Legacy Systems:** Many enterprises have legacy systems that need to be integrated with new applications, which can be difficult due to outdated technologies or lack of documentation. Migrating data from legacy systems to new applications can be a challenging and error-prone process.
	3. **Scalability:** As the organization grows, the application must handle an increasing number of users and transactions without degrading performance.
	4. **Security:** Enterprise applications often handle sensitive data, necessitating robust security measures to prevent data breaches and comply with regulations.
	5. **Data Management:** Ensuring the accuracy, consistency, and quality of data across various systems can be challenging. Many applications require real-time data processing and analytics, which can be difficult to implement and manage.
	6. **User Experience:** Creating a user-friendly interface that meets the needs of diverse user groups can be challenging, especially for complex applications. Users may require training to effectively use the application, which can add to the overall cost and time of deployment.
	7. **Deployment & maintenance:** Implementing a CI/CD pipeline can be complex, especially in large organizations with multiple teams.
	8. **Team Coordination and Communication:** Coordinating between multiple teams (development, operations, business analysts) can be challenging, especially in large organizations.
	9. **Cost Management:** Balancing functionality with budgetary constraints can be difficult, especially for large projects with significant scope.

#### <span style="color:blue;">12. List and explain Java Container Types.</span>
1. In Java EE, a **container** is a runtime environment that provides various services to components such as servlets, JavaServer Pages (JSP), Enterprise JavaBeans (EJB), and other Java applications.
2. Different types of containers serve specific purposes and provide various functionalities.
3. Here’s a list of the primary container types:
	1. **Web Container (Servlet Container):** It manages Servlets, JSPs. The complete life cycle fo servlet is managed by Servlet Container.
	2. **EJB Container:** It handles all aspects of an enterprise bean's operation within the application server and acts as an intermediary between the user-written business logic within the bean and the rest of the application server environment.
	3. **Application Client Container:** It manages the execution of Java EE application client components (application clients), which are used to access a variety of Java EE services (such as JMS resources, EJB components, web services, security, and so on.) from a JVM outside the Oracle GlassFish Server
	4. **Message Driven Bean Container:** Part of the EJB container, specifically designed to manage message-driven beans, which are asynchronous components that respond to messages from a messaging system (like JMS).
	5. **Java EE Connector Architecture (JCA) Container:** Manages resource adapters that allow Java EE applications to connect to various enterprise information systems (EIS), such as databases, ERP systems, or legacy systems.

#### <span style="color:blue;">13. What is CGI? What are alternatives to cgi? Explain in detail.</span>
1. **Common Gateway Interface (CGI)** is a standard protocol that allows web servers to execute external programs or scripts to generate dynamic content. When a web server receives a request for a CGI script, it processes the request by invoking the specified program, passing input data, and returning the output to the client as part of the HTTP response.
2. Challenges of CGI:
- **Performance**: Each request spawns a new process, which can lead to overhead and slower response times, especially under high load.
- **Concurrency**: Handling multiple requests simultaneously can be challenging, as each request runs in its own process, leading to resource consumption issues.
- **State Management**: Managing user sessions and maintaining state across multiple requests can be complex with CGI.
3. Due to the limitations of CGI, several alternatives have emerged, offering more efficient ways to handle dynamic content on the web. Here are some of the most popular alternatives:
	1. **FastCGI:** FastCGI is an improvement over CGI that keeps the process alive to handle multiple requests, reducing the overhead of starting a new process for each request.
	2. **PHP:** PHP is a popular server-side scripting language that is widely used for web development. It is designed to be embedded in HTML pages and can be used to generate dynamic content.
	3. **Java Servlets:** Java Servlets are Java-based alternatives to CGI that are designed to be more scalable and efficient. They can handle large volumes of traffic and can be used to generate dynamic content.
	4. **Web Frameworks:** Web frameworks like Django, Ruby on Rails, and Flask provide a more structured and efficient way to develop web applications. They abstract away many of the low-level details of web development and provide features like URL routing, templating, and database integration.

#### <span style="color:blue;">14. Explain deployment descriptor file with its elements in ejava.</span>
1. In Java EE (Enterprise Edition), a **deployment descriptor** is an XML file that describes the configuration and deployment settings for a Java EE application.
2. It plays a crucial role in defining how components interact with each other and how they are managed by the application server.
3. Deployment descriptor file includes:
	1. **web.xml:** It is used for web applications, it provides information about the application's configuration, classes, resources and more.
	2. **ejb-jar.xml:** It contain structural and application assembly information for an enterprise bean
	3. **persistence.xml:** It is standard configuration file for JPA
**Common Elements in web.xml:**
1. **`<web-app>`**: The root element, which defines the web application and its version.
2. **`<servlet>`**: Declares a servlet and its configuration, including:
	1. **`<servlet-name>`**: Unique name for the servlet.
	2. **`<servlet-class>`**: Fully qualified class name of the servlet.
	3. **`<init-param>`**: Initialization parameters for the servlet.
3. **`<servlet-mapping>`**: Maps a servlet to a specific URL pattern.
4. **`<filter>`**: Defines a filter to process requests/responses
5. **`<welcome-file-list>`**: Specifies the default page(s) when a directory is requested.
6. **`<error-page>`**: Defines custom error pages for specific HTTP error codes.
**Common Elements in ejb-jar.xml:**
1. **`<ejb-jar>`**: Root element for EJB configurations.
2. **`<enterprise-bean>`**: Defines an EJB component, including:
	1. **`<ejb-name>`**: Unique name for the EJB.
	2. **`<jboss-home>`**: Home interface for the EJB (for CMP beans).
3. **`<persistence-context>`**: Configures persistence context for entity beans.
**Common Elements in persistence.xml:**
1. **`<persistence>`**: Root element for JPA configurations.
2. **`<persistence-unit>`**: Defines a unit of work with properties such as:
	1. **`<provider>`**: JPA provider (e.g., Hibernate).
	2. **`<class>`**: Specifies entity classes.
	3. **`<properties>`**: Additional configurations (e.g., database connection settings).

#### <span style="color:blue;">15. Explain rowset and its type in jdbc.</span>
1. RowSet is an interface in java that is present in the javax.sql package.
2. **RowSet** is a powerful extension of the standard ResultSet interface, providing a more flexible and easier-to-use way of handling database data.
3. A RowSet is a wrapper around a ResultSet that adds features such as the ability to be disconnected from the database, to be easily serialized, and to work with JavaBeans properties.
4. A JDBC RowSet provides a way to store the data in tabular form. It makes the data more flexible and easier than a ResultSet.
5. The connection between the RowSet object and the data source is maintained throughout its life cycle.
6. Types of RowSet:
1. **JdbcRowSet:** A connected RowSet that uses JDBC to connect to a database and execute SQL queries.
	- **Key Features**:
	    - Automatically opens a connection to the database.
	    - Can be updated and committed to the database.
	    - Provides a way to retrieve data in a tabular format.
	- **Usage**: Typically used for simple operations where the application needs to read and write data directly to a database.
2. **CachedRowSet:** A disconnected RowSet that stores data in memory, allowing for manipulation without maintaining a database connection.
	- **Key Features**:
	    - Supports scrolling through the data.
	    - Allows changes to be made locally and then sent back to the database in a single transaction.
	    - Can be serialized, making it suitable for use in distributed applications.
	- **Usage**: Useful in scenarios where you want to work with data offline and synchronize changes later.
3. **MappedRowSet:** A type of CachedRowSet that maps its columns to the properties of a JavaBean.
	- **Key Features**:
	    - Provides a way to easily bind data to JavaBeans, enhancing data manipulation.
	    - Supports reading and writing of data while maintaining the relationship between the database and the JavaBean properties.
	- **Usage**: Ideal for applications that need to integrate database data directly with JavaBeans, allowing for easier data management.
4. **WebRowSet:** A specialized RowSet that can be used for exchanging data between a database and a web application using XML.
	- **Key Features**:
	    - Supports serialization of data in XML format.
	    - Useful for transferring data over a network or for web services.
	- **Usage**: Best suited for applications that require data interchange over HTTP or other web protocols.