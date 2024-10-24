#### <span style="color:blue;">1. Distinguish between servlet and jsp.</span>

| JSP                                                                                                                        | Servlet                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| 1. JSP is a technology that allows the creation of dynamic web content using HTML and Java code.                           | 1. A Servlet is a Java class that handles requests and responses in a web application.                                    |
| 2. Uses a mix of HTML and JSP tags (e.g., `<% %>` for Java code).                                                          | 2. Pure Java code with the implementation of `HttpServlet` class.                                                         |
| 3. Easier to write and maintain, especially for designers familiar with HTML.                                              | 3. More complex due to Java syntax and structure, requiring more coding.                                                  |
| 4. Encourages separation of presentation and business logic using JSP tags and EL (Expression Language).                   | 4. Typically combines presentation and business logic, making it harder to separate concerns.                             |
| 5. Compiled into a servlet by the JSP container before execution.                                                          | 5. Compiled and executed directly as a Java class.                                                                        |
| 6. The lifecycle is managed by the JSP container; includes translation, compilation, initialization, and execution phases. | 6. The lifecycle is managed by the servlet container, involving initialization, request handling, and destruction phases. |
| 7. Can be less performant for small requests since JSPs are compiled into servlets, adding an initial overhead.            | 7. Generally faster for complex business logic due to direct execution of Java code.                                      |
| 8. Easier error handling with custom error pages and `try-catch` blocks.                                                   | 8. More complex error handling, often requiring explicit management.                                                      |
| 9. Supports session management via JSP implicit objects (e.g., `session`).                                                 | 9. Also supports session management but requires more explicit handling.                                                  |
| 10. Best for creating the user interface of web applications with dynamic content.                                         | 10. Best for processing requests, performing business logic, and handling data.                                                                                                                      |
#### <span style="color:blue;">2. Explain life cycle of jsp with diagram.</span>
![JSP Life Cycle.png](https://github.com/ggk570/Bsc-IT-Sem-5/blob/main/Advance%20Java%20Technologies/Solved%20Question%20Papers/Images/JSP%20Life%20Cycle.png)

The life cycle of JSP is as follows:
1. **Translation:** When a jsp page is accessed for the first time, it is translated into a servlet by the JSP Container. The JSP container creates a servlet class that extends HttpServlet class and contains the code for the JSP Page.
2. **Compilation:** The servlet class is then compiled into bytecode by the Java compiler.
3. **Initialization:** The JSP Container creates an instance of the translated servlet class and calls the init() method. This method is used to perform any initialization tasks that need to be done before the servlet can handle requests.
4. **Request Handling:** When a client sends a request to a jsp page, the jsp container calls the service() method of servlet class. This methods handles request and generates response.
5. **Destruction:** When the jsp container shuts down or the jsp page is removed, the container calls the destroy() method of servlet class to perform cleanup task and reclaim memory.
6. **Recompile:** If the jsp page is modified, the jsp container recompiles it into servlet and replaces old servlet with new one. This allows jsp page to be updated without restarting the server.

#### <span style="color:blue;">3. Explain different types of JSP tags with example.</span>
JSP (JavaServer Pages) tags are used to embed Java code and perform various functions in JSP pages. There are several types of JSP tags, each serving a different purpose. Here’s an overview of the main types of JSP tags along with examples:
1. **Directive Tags:** Directive tags provide global information about an entire JSP page. They are used to set properties for the JSP engine.
	**Example:** Setting the content type and page encoding
	`<%@ page contentType="text/html;charset=UTF-8" language="java" %>`
2. **Declaration Tags:** Declaration tags allow you to declare variables and methods that can be used later in the JSP page. These declarations are placed inside `<%! %>` tags. When the jsp page is converted into actual servlet the declaration content goes inside the servlet class but outside the service() method.
	**Example:** Declaring a variable in a JSP.
	`<%! public String name = "John"; %>`
3. **Scriplet Tags:** Scriptlet tags allow you to embed Java code directly into the HTML. They are placed inside `<% %>` tags. This portion of code goes directly in service() method of servlet class.
	**Example:** Using a scriptlet to display a greeting message.
	`<% out.println("Welcome " + name); %>`
4. **Expression Tags:** Expression tags are used to output data directly to the client. They are written inside `<%= %>` tags.
	**Example:** Displaying a dynamic value.
	```
	<%
	    String time = new java.util.Date().toString();
	%>
	<p>The current time is: <%= time %></p>
	```
5. **Action Tags:** Action tags are used to perform actions like including other resources or forwarding requests. They are defined by the JSP specification.
	**Example:** Including another JSP file.
	`<jsp:include page="header.jsp" />`
6. **Standard Tags (JSTL):** The JSP Standard Tag Library (JSTL) provides a set of tags for common tasks such as iteration, conditionals, and internationalization.
	**Example:** Using JSTL for iteration.
	```
	<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
	<c:forEach var="item" items="${itemList}">
	    <p>${item}</p>
	</c:forEach>
	```

#### <span style="color:blue;">4. Explain different core tags in JSTL.</span>
1. JSTL (JavaServer Pages Standard Tag Library) provides a collection of tags that simplify the development of JSP pages. These tags are categorized into different libraries based on their functionality.
2. The core tags in JSTL are used for common tasks like conditionals, loops, and variable manipulation.
3. Before using JSTL tags, you need to include the tag library in your JSP page:
	`<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>`
4. Here’s an overview of the main core tags along with examples:
- **<c:if>**: Used for conditional processing. If the condition evaluates to true, the body is executed.
	`<c:if test="${user.loggedIn}"> Welcome, ${user.name}! </c:if>`
- **<c:choose>**: A more complex conditional structure that allows multiple conditions using `<c:when>` and `<c:otherwise>`.
	```
	<c:choose>
	<c:when test="${user.role == 'admin'}">
		Admin Access
	</c:when>
	<c:otherwise>
		User Access
	</c:otherwise>
	</c:choose>
	```
- **<c:forEach>**: Used for iterating over a collection (like a list or array).
	```
	<c:forEach var="item" items="${itemList}"> <p>${item}</p> </c:forEach>
	```
- **<c:forTokens>**: Used for splitting a string into tokens based on a specified delimiter.
	```
	<c:forTokens var="token" items="${myString}" delims=","> <p>${token}</p> </c:forTokens>
	```
- **<c:import>**: Used to include content from another resource, like a JSP or HTML page.
	`<c:import url="header.jsp" />`
- **<c:set>**: Used to define or modify a variable in the current scope.
	`<c:set var="message" value="Hello, World!" /> <p>${message}</p>`
- **<c:remove>**: Removes a variable from the specified scope.
	`<c:remove var="message" scope="session" />`
- **<c:out>**: Outputs data to the client, escaping XML characters automatically.
	`<c:out value="${user.name}" />`
- **<c:param>**: Adds parameters to a URL or included resource.
	`<c:param name="id" value="${user.id}" />`
- **<c:redirect>**: Redirects the user to another URL (only available in JSTL 1.2).
	`<c:redirect url="success.jsp" />`

#### <span style="color:blue;">5. List and explain any 4 JSP implicit objects with their methods.</span>
JavaServer Pages (JSP) provide several implicit objects that simplify the development of web applications. Here are four key JSP implicit objects along with their methods:
1. **request**
    - **Description**: Represents the client's request to the server. It is an instance of `HttpServletRequest` and contains data such as form parameters, request headers, and attributes.
    - **Common Methods**:
        - `getParameter(String name)`: Retrieves the value of a form parameter by its name.
        - `getAttribute(String name)`: Returns an object associated with the specified attribute name.
        - `getHeader(String name)`: Returns the value of a specified request header.
2. **response**
    - **Description**: Represents the server's response to the client. It is an instance of `HttpServletResponse` and is used to send data back to the client.
    - **Common Methods**:
        - `setContentType(String type)`: Sets the MIME type of the response.
        - `sendRedirect(String location)`: Sends a temporary redirect response to the client using the specified location.
        - `getWriter()`: Returns a `PrintWriter` object to send character text to the client.
3. **session**
    - **Description**: Represents the session data for a specific user. It is an instance of `HttpSession` and allows you to store and retrieve user-specific data across multiple requests.
    - **Common Methods**:
        - `getAttribute(String name)`: Retrieves an object associated with the specified session attribute name.
        - `setAttribute(String name, Object value)`: Stores an object in the session under the specified attribute name.
        - `invalidate()`: Invalidates the session, removing all session data.
4. **application**
    - **Description**: Represents the servlet context for the entire web application. It is an instance of `ServletContext` and is used for application-wide settings and attributes.
    - **Common Methods**:
        - `getAttribute(String name)`: Retrieves an object associated with the specified application-wide attribute name.
        - `setAttribute(String name, Object value)`: Stores an object in the application context.
        - `getInitParameter(String name)`: Returns the value of a specified initialization parameter defined in the web application’s deployment descriptor (web.xml).

#### <span style="color:blue;">6. Explain different scope of JSP objects.</span>
In JSP, different scopes determine the lifespan and visibility of objects. There are four main scopes: **page**, **request**, **session**, and **application**.
Each scope serves a different purpose and is used to manage data in various contexts. Here's a detailed explanation of each scope:
1. **Page Scope**
- **Description**: Objects created in this scope are available only within the current JSP page. They are accessible only during the processing of the page itself.
- **Lifespan**: The object exists as long as the page is being processed.
- **Usage**: Ideal for temporary data that doesn't need to persist beyond a single page.
2. **Request Scope**
- **Description**: Objects stored in the request scope are accessible across different components (e.g., JSP pages, servlets) that handle the same request. This scope is used to share data during the life of a single request.
- **Lifespan**: The object exists until the response is committed and sent back to the client.
- **Usage**: Suitable for passing data between different parts of the application in response to a single user action.
3. **Session Scope**
- **Description**: Objects in the session scope are available to all requests from the same user session. This means that data can persist across multiple pages and requests for a single user.
- **Lifespan**: The object remains valid until the session is invalidated (e.g., user logs out) or times out (based on server settings).
- **Usage**: Ideal for storing user-specific information, like login credentials, shopping cart contents, or user preferences.
4. **Application Scope**
- **Description**: Objects in the application scope are shared across all users and sessions. This means that data stored here is accessible from any JSP or servlet within the same web application.
- **Lifespan**: The object lasts for the entire duration of the web application until it is explicitly removed or the application is stopped.
- **Usage**: Suitable for storing application-wide configuration settings or resources that need to be shared across multiple users (e.g., global counters, database connection pools).

#### <span style="color:blue;">7. Give explanation of the jsp:useBean action tags attribute and usage.</span>
1. The `<jsp:useBean>` action tag in JSP is used to instantiate and manage JavaBeans within a JSP page.
2. It provides a way to create or reuse a JavaBean object, making it easier to access the properties of that bean within the JSP.
3. Attributes of `<jsp:useBean>`:
	1. **id:** Specifies the name of the bean instance to be created or accessed. This name is used as a reference in the JSP page. It must be unique within the scope of the page.
	2. **class:** Specifies the fully qualified name of the JavaBean class that you want to create or use. Required attribute. It tells the JSP which Java class to instantiate.
	3. **scope:** Defines the scope of the bean. It can be one of the following values: `page`, `request`, `session`, or `application`. If not specified, the default scope is `page`.
	4. **type:** Specifies the type of the bean. This is useful for specifying the type of the bean if the `class` attribute is not used or if you want to enforce type checking.
	5. **beanName:** This was used to specify a name for the bean. It is now replaced by the `id` attribute.

#### <span style="color:blue;">8. Write a short note on jsp:plugin action.</span>
1. The `<jsp:plugin>` action in JSP is used to embed applets or other types of plugins into a web page.
2. This action tag simplifies the process of generating the necessary HTML or JavaScript code for browser plugins, ensuring cross-browser compatibility.
3. Key Attributes
	1. **type**:
	    - **Description**: Specifies the type of plugin being used. Common values include `applet` and `object`.
	    - **Usage**: Determines how the plugin will be rendered in the browser.
	2. **code**:
	    - **Description**: Defines the codebase of the applet or plugin class. This is typically the fully qualified name of the Java class.
	    - **Usage**: Required when the type is `applet`.
	3. **codebase**:
	    - **Description**: Specifies the URL where the plugin classes or resources can be found.
	    - **Usage**: Helps the browser locate the necessary files.
	4. **width** and **height**:
	    - **Description**: Define the dimensions of the plugin in pixels.
	    - **Usage**: Control the size of the display area for the plugin.
	5. **align**:
	    - **Description**: Determines the alignment of the plugin in relation to surrounding content.
	    - **Usage**: Common values include `left`, `right`, `top`, and `bottom`.
	6. **alt**:
	    - **Description**: Provides alternative text to display if the plugin cannot be loaded.
	    - **Usage**: Enhances accessibility and user experience.
```
<jsp:plugin type="applet" code="com.example.MyApplet" codebase="/applet" width="300" height="200">
    <jsp:params>
        <jsp:param name="param1" value="value1" />
        <jsp:param name="param2" value="value2" />
    </jsp:params>
    <jsp:plugin>
        <param name="alt" value="Java applet cannot be loaded." />
    </jsp:plugin>
</jsp:plugin>
```

#### <span style="color:blue;">9. What is exactly JSTL and describe XPath in detail.</span>
1. JSTL stands for JavaServer Pages Standard Tag Library, which is a collection of JSP tags that encapsulate core functionality common to many JSP applications.
2. JSTL provides a set of tags that can be used to perform common tasks such as looping over collections, formatting data, and conditional processing.
3. JSTL is designed to simplify JSP development by providing a standard set of tags that can be used across different JSP containers.
4. XPath is a language used for selecting nodes from an XML document
5. XPath is used to navigate through elements and attributes in an XML document and is used by many XML-related technologies, including XSLT, XQuery, and XML Schema. XPath uses a path-like syntax to identify nodes in an XML document.
6. XPath expressions are used to select nodes in an XML document.
7. XPath expressions can be used to select nodes based on their name, value, or position in the document.
8. XPath expressions are evaluated against an XML document and return a set of nodes that match the expression.
9. XPath expressions can use a variety of operators and functions to select nodes.

#### <span style="color:blue;">10. What is Expression Language? What are types of EL?</span>
1. **Expression Language (EL)** is a feature in JavaServer Pages (JSP) that allows developers to access and manipulate data in a simple and readable manner.
2. It provides a way to evaluate expressions, access data stored in JavaBeans, collections, and other objects, making it easier to work with dynamic content in JSP pages.
3. Key Features of Expression Language (EL):
	- **Simplicity**: EL syntax is designed to be easy to read and write, making it more accessible for developers compared to using scriptlets.
	- **Automatic Resolution**: EL automatically resolves variables, allowing developers to access properties without needing to use getter methods explicitly.
	- **Implicit Objects**: EL can access implicit objects (like request, session, application, etc.) without needing to explicitly declare them.
4. Types of Expression Language
	1. **Simple Expressions:** These access variables directly.
		Example: `${user.name}`
		This accesses the `name` property of the `user` object.
	2. **Arithmetic Expressions:** We can perform arithmetic operations directly.
		Example: `${5 + 10} // Outputs: 15`
	3. **Logical Expressions:** EL supports logical operations like AND, OR, and NOT.
		Example `${user.age > 18 && user.isActive}`
	4. **Relational Expressions:** You can compare values using relational operators `(==, !=, <, >, etc.)`.
		Example: `${user.age >= 21}`
	5. **Conditional Expressions:** Conditional (ternary) expressions can be used to evaluate conditions.
		Example: `${user.active ? 'Active' : 'Inactive'}`
	6. **Method Invocation:** You can invoke methods on objects.
		Example: `${user.getFullName()}`
	7. **Collection Access:** EL allows accessing elements in collections such as lists or maps.
		Example: `${userList[0].name}`
	8. **Map Access:** You can access entries in a map by using key expressions.
		Example: `${myMap['key']}`

#### <span style="color:blue;">11. Write a short note on restriction, projection and partitioning operators in EL.</span>
1. **Restriction operator – where**: Iterates over the source sequence and yields those elements for which the predicate function returns true.
2. The predicate function accepts two arguments: The first one represents the element to test The second, if present, represents the zero-based index of the element within the source sequence. e.g. employees.where(e->e.salary >=10000)
3. **Projection operator – select**: Iterates over the source sequence and yields the results of evaluating the selector Lambda for each element.
4. The selector accepts two arguments: The first one represents the element to process The second, if present, represents the zero-based index of the element within the source sequence. e.g. employees.select(e->e.EmployeeName)
5. **Partitioning operator – take** : Iterates over the source sequence and yields a given number of elements from a sequence and then skips the remainder of the sequence. e.g. employees.take(100).
6. **Partitioning operator – skip**: Iterates over the source sequence and skips a given number of elements from a sequence and then yields the remainder of the sequence. e.g. employees.skip(2)

#### <span style="color:blue;">12. How to query and update data in JSTL.</span>
1. To query and update data in JSP using JSTL (JavaServer Pages Standard Tag Library), we can utilize the SQL tag library, which allows us to interact with databases directly from your JSP pages. Here's a detailed guide on how to do this effectively.
2. First include the JSTL SQL library in your JSP file. We might need to add the JSTL library to our project dependencies if it's not already included.
	`<%@ taglib uri="http://java.sun.com/jsp/jstl/sql" prefix="sql" %>`
3. We need to set up a data source that connects to your database. This is typically done using the `<sql:setDataSource>` tag.
```
<sql:setDataSource var="dataSource"
    driver="com.mysql.jdbc.Driver"
    url="jdbc:mysql://localhost:3306/dbname"
    user="username" 
    password="password" />
```
4. We can then can use the `<sql:query>` tag to execute SQL SELECT statements and retrieve data from the database.
```
<sql:query var="result" dataSource="${dataSource}"> 
	SELECT * FROM users;
</sql:query>
<c:forEach var="row" items="${result.rows}">
	<p>ID: ${row.id}, Name: ${row.name}, Age: ${row.age}</p>
	<a href="updateUser.jsp?id=${row.id}">Edit</a>
</c:forEach>
```
5. To update data, we can use the `<sql:update>` tag. Typically, we would have a form where the user can input new data.
```
<sql:update dataSource="${dataSource}">
	UPDATE users SET name = ?, age = ? WHERE id = ?
	<sql:param value="${param.name}" />
	<sql:param value="${param.age}" />
	<sql:param value="${param.id}" />
</sql:update>
```
