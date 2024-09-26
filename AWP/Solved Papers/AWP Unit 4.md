##### <span style="color:blue;">1. Explain the data provider model with ADO.Net with diagram.</span>
![[Screenshots/ADO.png]]
1. ADO.NET is a data access technology from Microsoft that is part of the .NET Framework. It provides a set of classes and interfaces for interacting with a variety of data sources, such as databases, XML files, and more.
2. The data provider model is a fundamental concept in ADO.NET, acting as the bridge between your application and various data sources. It provides a way to connect to different types of data sources, execute commands, and retrieve results in a consistent manner.
3. The different data providers in ADO.Net includes:

| Data Provider        | Api Prefix | Description                                                                                                                                                                                              |
| -------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ODBC Data Provider   | Odbc       | Data Sources with an ODBC interface. Normally older databases like MySQL                                                                                                                                 |
| OleDB Data Provider  | OleDb      | Data Sources that expose an OleDb interface. It is windows specific only. It allows applications to access data from a variety of sources, including file systems, personal databases, spreadsheets etc. |
| Oracle Data Provider | Oracle     | For oracle databases.                                                                                                                                                                                    |
| SQL Data Provider    | Sql        | For interacting with Microsoft Sql Server.                                                                                                                                                               |

5. Core components of data provider includes:
	1. **Connection:** It is used to establish a connection to a specific data source like Sql Server, Oracle etc. E.g SqlConnection for Sql Server, OleDbConnection for OLE DB Sources, OdbcConnection for ODBC sources.
	2. **Command:** It is used to execute queries to perform database operations. Commands can be SQL statements or stored procedures. E.g SqlCommand, OleDbCommand etc
	3. **DataReader:** It is used to read data from data source. The DbDataReader is a base class for all DataReader objects. It's efficient for retrieving large amounts of data as it doesn't load all results into memory at once. E.g SqlDataReader, OleDbDataReader etc.
	4. **DataSet:** It is an in-memory data store that can hold more than one table at the same time. It is disconnected from the database, allowing data manipulation and storage without constant database connections.
	5. **DataTable:** A part of the DataSet, representing a single table of in-memory data.
	6. **DataAdapter:** Acts as a bridge between the DataSet and the database. It uses commands to populate the DataSet and can also update the database with changes made to the DataSet. E.g SqlDataAdapter, OleDbDataAdapter.
6. Data providers works by first establishing a connection to database by using connection class like SqlConnection.
7. We would then need to instantiate a command object to create commands, e.g SqlCommand object. We can set it's properties including sql query or stored procedure.
8. To execute our query we can use methods like `ExecuteReader` for reading data, `ExecuteNonQuery` for executing commands that don’t return results, and `ExecuteScalar` for single value queries.
9. To read data we can use DataReader object, using this we can can iterate through the results in a forward-only manner. For disconnected scenarios we can use a DataAdapter object to fill DataSet.
10. With DataSet and DataTable object we can insert, update or delete rows. Any changes to the dataset can be pushed to database using DataAdapter's Update method.

##### <span style="color:blue;">2. Write a short note on connected and disconnected data access.</span>
**Connected Data Access:**
1. In connected data access, an application maintains an active connection to the database for the duration of data operations.
2. This model is often used when immediate, real-time data interaction is required.
3. We typically employ the DataReaderclass object for connected data access. DataReader is used to retrieve data from databases. 
4. In this type we can read data in forward only manner which means if we have access data in a particular row then we can access data in next rows, we can't access data in previous rows. Hence if we want to access previous rows then we need to create variables and store data in them for later use.
5. This type of data access gives faster performance when dealing with small application and less data.
6. Changes to database needed to done on real time basis.
7. Requires more resources as connections must be managed, which can lead to scalability issues and deadlocks risks or resource conflicts in multi-user environments.
**Disconnected Data Access:**
1. In disconnected data access, the application retrieves data from the database, stores it in memory (like in a `DataSet`), and works with it without maintaining an ongoing connection to the database.
2. This model is used when no real-time data interaction is required. 
3. In this type Data is loaded into a DataSet or DataTable object, allowing for retrieval or manipulation of data on demand without an active database connection.
4. Unlike connected data access, we can read any data at any time there is no forward only read restriction.
5. This gives best performance when dealing with multi-layered applications and loads of data.
6. Changes can be made to dataset or datatable, these changes can be commited to database at any time by connecting to the database and then disconnecting once the task is finished. Also changes can be sent back to the database in batches, optimizing performance.
7. Since it is not connection oriented it reduces the load on database server. Thus it is more scalable, reliable especially in scenarios with many users.

##### <span style="color:blue;">3. Write a brief explanantion of the types of Asp.Net data binding.</span>
1. Data binding in ASP.NET is the process of connecting a data source to a control, such as a list box or data grid. This connection allows data to be displayed in the control, and any changes to the data are automatically reflected in the user interface.
2. Every ASP.NET web form control inherits the DataBind method from its parent Control class, which gives it an inherent capability to bind data to at least one of its properties.
3. We can connect these controls to ADO.NET components such as a DataView, DataSet, or DataViewManager or even arrays, lists at design-time as well as at run-time.
4. **Types of ASP.Net data binding:**
	1. **Single Value Data Binding:** Single value data binding in ASP.NET refers to the process of binding a single piece of data (like a string, number, or object property) to a control, rather than a collection of data. This is commonly used for displaying or editing a single value in UI elements like labels, text boxes, or other controls.
	- It is implemented with the syntax
		`<%#Expression%>`
	- In the above syntax we can replace the expression with any string, int, object property or even call a method, the return value would be assigned to a property of a control
	- To use this type of binding we need to call the **DataBind()** method on our page class, this can be done by writing below code in Page_Load event handler:
		`this.DataBind();`
	- E.g Lets assume a public field strName is already been defined in codebehind file
		`<asp:Label runat="server" ID="Label1" Text="<%# strName %>"></asp:Label>`
	2. **Repeated Value Data Binding:** Repeated value data binding in ASP.NET refers to binding a collection of data items to a control that can display multiple items, such as lists or grids
	- This allows us to show repeated values, like records from a database or items from a list, in a structured format.
	- Examples of controls that supports this type of data binding includes:
		GridView, ListView, FormView, DetailsView, ListBox, DataList, DropDownList, Repeater etc.
	- These controls use the DataSource property to bind to a database or collection.
	- To use repeated value data binding, first we need to create a control capable of repeated value data binding, then we can create and fill data object, for this we can use any type of collection like ArrayList, Hashtable, Dictionary, Data Table, Data set object. After this we can link the data object to control with DataSource property. To activate the binding we need to call DataBind() method on the control.
	- Example
	**WebForm1.aspx**
	```
	<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="DatabindPractice.WebForm1" %>
	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml">
	<head runat="server">
    <title></title>
	</head>
	<body>
    <form id="form1" runat="server">
        <div>
            <asp:Repeater ID="rptCountries" runat="server">
                <HeaderTemplate>
                    <h3>Countries List</h3>
                </HeaderTemplate>
                <ItemTemplate>
                    <div>
                        <%# Container.ItemIndex + 1 %>
                        <%# ((Country)Container.DataItem).CountryName %>
                    </div>
                </ItemTemplate>
                <FooterTemplate>
                    <br />
                    <div>Copyright 2024</div>
                </FooterTemplate>
            </asp:Repeater>
        </div>
    </form>
	</body>
	</html>
	```
	**WebForm1.aspx.cs**
	```
	using System;
	using System.Collections.Generic;
	namespace DatabindPractice
	{
	    public partial class WebForm1 : System.Web.UI.Page
	    {
	        protected void Page_Load(object sender, EventArgs e)
	        {
	            if (!IsPostBack)
	            {
	                // Sample data source
	                var countries = new List<Country>
		            {
		                new Country("India"),
		                new Country("USA"),
		                new Country("Japan"),
		                new Country("UK"),
		                new Country("Netherlands"),
		                new Country("Australia"),
		                new Country("Sri Lanka"),
		            };
	                // Bind the data to the Repeater
	                rptCountries.DataSource = countries;
	                rptCountries.DataBind();
	            }
	        }
	    }
	}
	public class Country
	{
	    public String CountryName { get; set; }
	    public Country(String name) { CountryName = name; }
	}
	```

##### <span style="color:blue;">4. Explain page life cycle with data binding.</span>
1. The ASP.NET page life cycle is a series of events that occur from the time a page is requested until it is fully rendered and sent to the client.
2. Key stages of Asp.Net page life cycle:
- **Page Request:** The life cycle begins when a request for a page is received by the server.
- **Start:** The ASP.NET application determines whether the request is for a new page or a postback (when a form is submitted).
- **Init:** During page initialization, controls on the page are available and each control's UniqueID property is set. A master page and themes are also applied to the page if applicable.. It's generally not advisable to bind data here because the control tree isn’t fully created yet.
- **Load:** During this phase, the page and its controls are loaded with data from the view state, allowing the state to be preserved across postbacks. This is a critical point for data binding. You can bind data to controls here, especially when not dealing with postbacks. For postbacks, ensure you check `!IsPostBack` to avoid re-binding and losing user input.
- **Post Back Event Handling:** If the page is a postback, any control event handlers (like button clicks) are executed. This is where user interactions are processed. Data can be updated based on user input here, allowing for dynamic changes based on user actions.
- **Rendering:** The page calls the `Render` method for each control, generating the HTML to be sent to the client. At this point, the view state is not accessible for data binding. Controls are rendered based on their current state, and data binding should have already been completed.
- **Unload:** The page and its controls are cleaned up. This is the final stage where resources can be released, and any final processing can occur.

##### <span style="color:blue;">5. Explain gridview control and its method for defining columns.</span>
1. The GridView control displays data in a table format with rows and columns, where each column represents a field and each row represents a record.
2. The [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control supports the following features:
- Binding to data source controls, such as [SqlDataSource](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.sqldatasource?view=netframework-4.8.1).
- Built-in sort capabilities.
- Built-in update and delete capabilities.
- Built-in paging capabilities.
- Built-in row selection capabilities.
- Programmatic access to the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) object model to dynamically set properties, handle events, and so on.
- Multiple key fields.
- Multiple data fields for the hyperlink columns.
3. **Properties of GridView:**

| Property     | Description                                                                                                       |
| ------------ | ----------------------------------------------------------------------------------------------------------------- |
| DataSourceID | ID assigned to the DataSource.                                                                                    |
| AllowSorting | It is a boolean value. True value generates clickable column headers that sort the column's data when selected.   |
| AllowPaging  | It is a boolean value indicating whether control will provide paging with page size defined in PageSize property. |
| PageSize     | No of records included in one page                                                                                |
| BackColor    | Background color                                                                                                  |
| BorderColor  | Color name or hex value assigned to GridView's border                                                             |
4. Each column in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control is represented by a [DataControlField](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.datacontrolfield?view=netframework-4.8.1) object. By default, the [AutoGenerateColumns](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview.autogeneratecolumns?view=netframework-4.8.1) property is set to `true`, which creates an [AutoGeneratedField](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.autogeneratedfield?view=netframework-4.8.1) object for each field in the data source. Each field is then rendered as a column in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control in the order that each field appears in the data source.
5. You can also manually control which column fields appear in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control by setting the [AutoGenerateColumns](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview.autogeneratecolumns?view=netframework-4.8.1) property to `false` and then defining your own column field collection. Different column field types determine the behavior of the columns in the control. The following table lists the different column field types that can be used.

| Column Field Type | Description                                                                                                                                                                                                                                                                           |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BoundField        | Displays the value of a field in a data source. This is the default column type of the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control.                                                                   |
| ButtonField       | Displays a command button for each item in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control. This enables you to create a column of custom button controls, such as the Add or the Remove button.      |
| CheckBoxField     | Displays a check box for each item in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control. This column field type is commonly used to display fields with a Boolean value.                                |
| CommandField      | Displays predefined command buttons to perform select, edit, or delete operations.                                                                                                                                                                                                    |
| HyperLinkField    | Displays the value of a field in a data source as a hyperlink. This column field type enables you to bind a second field to the hyperlink's URL.                                                                                                                                      |
| ImageField        | Displays an image for each item in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control.                                                                                                                   |
| TemplateField     | Displays user-defined content for each item in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control according to a specified template. This column field type enables you to create a custom column field. |
6. To define a column field collection declaratively, first add opening and closing `<Columns>` tags between the opening and closing tags of the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control. Next, list the column fields that you want to include between the opening and closing `<Columns>` tags. The columns specified are added to the [Columns](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview.columns?view=netframework-4.8.1) collection in the order listed. The [Columns](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview.columns?view=netframework-4.8.1) collection stores all the column fields in the control and enables you to programmatically manage the column fields in the [GridView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.gridview?view=netframework-4.8.1) control.

##### <span style="color:blue;">6. Write a short note on detailsview.</span>
1. DetailsView control used to display a single database record of table layout in ASP.Net. Means it works with a single data item at a time.
2. DetailsView control allows users to display, edit, delete and insert records.
3. **Properties of DataView:**
- **AutoGenerateRows:** Boolean value that specifies whether the control automatically generates rows for data fields. When set to `true`, it creates rows for all fields in the data source.
- **DataKeyNames:** String value that specifies the name of the field(s) that serve as the primary key. This is used to uniquely identify records in the data source.
- **DataSource:** The data source that the DetailsView will be bound to, such as a DataTable, DataSet, or a collection of objects.
- **DataSourceID:** The ID of a data source control (like SqlDataSource or ObjectDataSource) to which the DetailsView binds automatically.
- **Field:** A collection of `DataControlField` objects that define the fields to display in the DetailsView. You can use `BoundField`, `TemplateField`, etc.
- **DefaultMode:** Sets the initial mode of the DetailsView (e.g., `ReadOnly`, `Edit`, or `Insert`).
4. To explicitly declare the row fields for a [DetailsView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.detailsview?view=netframework-4.8.1) control, first set the [AutoGenerateRows](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.detailsview.autogeneraterows?view=netframework-4.8.1) property to `false`. Next, add opening and closing `<Fields>` tags between the opening and closing tags of the [DetailsView](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.detailsview?view=netframework-4.8.1) control. Finally, list the row fields that you want to include between the opening and closing `<Fields>` tags.

##### <span style="color:blue;">7. Explain:</span>
**ExecuteNonQuery:**
1. The `ExecuteNonQuery` is a crucial method in ADO.NET, specifically within the `Command` class (such as `SqlCommand` or `OleDbCommand`). It is used to execute SQL statements that do not return any data, such as:
- **INSERT** statements (to add new records)
- **UPDATE** statements (to modify existing records)
- **DELETE** statements (to remove records)
- **DDL (Data Definition Language)** commands like `CREATE`, `ALTER`, and `DROP`
2. `ExecuteNonQuery` returns an integer that represents the number of rows affected by the SQL command executed. This allows you to confirm how many records were impacted by an operation.
3. Since it is intended for operations that do not return rows, you cannot use `ExecuteNonQuery` with commands that return results, such as `SELECT` statements. For retrieving data, you would typically use `ExecuteReader` or `ExecuteScalar`.
4. It is typically used with DML, DDL, DCL, DML.
5. General Syntax:
```
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connectionString = "your_connection_string_here";
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            connection.Open();

            string sql = "INSERT INTO Products (ProductName, Price) VALUES (@ProductName, @Price)";
            using (SqlCommand command = new SqlCommand(sql, connection))
            {
                command.Parameters.AddWithValue("@ProductName", "New Product");
                command.Parameters.AddWithValue("@Price", 19.99);

                int rowsAffected = command.ExecuteNonQuery();
                Console.WriteLine($"{rowsAffected} row(s) inserted.");
            }
        }
    }
}
```

**ExecuteScalar:**
1. The `ExecuteScalar` method is a part of ADO.NET's `Command` class (such as `SqlCommand` or `OleDbCommand`) and is used to execute a SQL query that returns a single value.
2. This method is particularly useful when you need to retrieve a single value from the database, such as an aggregate result (like `COUNT`, `SUM`, `MAX`, etc.) or a specific field from a query that returns only one row.
3. `ExecuteScalar` returns an object, which is the value of the first column of the first row in the result set returned by the query. If the query returns no results, it returns `null`.
4. It is designed for queries that return only one value. If the query could return multiple rows or columns, it will still only return the first column of the first row.
5. If any data is returned by the query, this method will return object type representing data, we need to do type casting to access value of the data.
6. `ExecuteScalar` is more efficient than using a `DataReader` or `DataSet` when you only need a single value because it minimizes the overhead involved in managing additional data structures.
7. General Syntax
```
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connectionString = "your_connection_string_here";
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            connection.Open();

            // Example query that retrieves a single value
            string sql = "SELECT COUNT(*) FROM Products";
            using (SqlCommand command = new SqlCommand(sql, connection))
            {
                // ExecuteScalar to get the count of products
                int productCount = (int)command.ExecuteScalar();
                Console.WriteLine($"Total number of products: {productCount}");
            }
        }
    }
}
```

**ExecuteReader:**
1. The `ExecuteReader` method is an essential function in ADO.NET, specifically within the `Command` class (such as `SqlCommand` or `OleDbCommand`). It is used to execute SQL commands that return multiple rows of data, such as `SELECT` statements.
2. This method provides a way to read and process the results in a forward-only, read-only manner.
3. This method works on DQL (Data Query Language).
4. `ExecuteReader` returns an instance of `IDataReader` (usually a `SqlDataReader` for SQL Server). This object provides a way to access the data returned by the SQL command.
5. The `DataReader` is designed to read data in a forward-only manner. Once you move past a row, you cannot go back. This makes it efficient for reading large datasets. The DataReader works by using Read method. It returns `true` as long as there are more rows to read.
6. ExecuteReader is generally more efficient than DataSet or DataAdapter in terms of memory usage.
7. General Syntax:
```
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connectionString = "your_connection_string_here";
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            connection.Open();

            // Example query that retrieves multiple rows
            string sql = "SELECT ProductID, ProductName, Price FROM Products";
            using (SqlCommand command = new SqlCommand(sql, connection))
            {
                // ExecuteReader to get the results
                using (SqlDataReader reader = command.ExecuteReader())
                {
                    // Read through the result set
                    while (reader.Read())
                    {
                        int productId = reader.GetInt32(0); // First column
                        string productName = reader.GetString(1); // Second column
                        decimal price = reader.GetDecimal(2); // Third column

                        Console.WriteLine($"ID: {productId}, Name: {productName}, Price: {price}");
                    }
                }
            }
        }
    }
}
```

##### <span style="color:blue;">8. Explain SqlDataSource Control.</span>
1. The SqlDataSource control can be used to access and modify data directly from a relational database, including Microsoft SQL Server, Microsoft Access, Oracle, MySQL, and others.
2. With this control we can use declarative data binding to perform database operations like update, insert, delete or query.
3. It simplifies the process of working with databases by allowing developers to manage data operations through properties and methods rather than writing extensive code.
4. We can can specify SQL commands (like `SELECT`, `INSERT`, `UPDATE`, and `DELETE`) directly in the control's properties, allowing for straightforward data retrieval and manipulation.
5. The `SqlDataSource` supports parameterized queries, which helps prevent SQL injection attacks and makes your queries more dynamic
6. It integrates seamlessly with data-bound controls like `GridView`, `DetailsView`, and `FormView`, making it simple to display and edit data on web pages.
7. The control automatically manages the database connection, opening and closing it as needed, which simplifies resource management.
8. **Properties:**
- **ConnectionString:** Specifies the connection string used to connect to the database.
- **SelectCommand:** Sql statement to retrieve data.
- **InsertCommand:** Sql statement used to insert data.
- **UpdateCommand:** Sql statement used to update existing records.
- **DeleteCommand:** The SQL statement used to delete records.
- **SelectParameters:** A collection that allows you to add parameters for the `SelectCommand`.
- **InsertParameters:** A collection for parameters used in the `InsertCommand`.
- **UpdateParameters:** A collection for parameters used in the `UpdateCommand`.
- **DeleteParameters:** A collection for parameters used in the `DeleteCommand`.
9. Example:
```
<asp:SqlDataSource 
    ID="SqlDataSource1" 
    runat="server" 
    ConnectionString="<%$ ConnectionStrings:YourConnectionString %>"
    SelectCommand="SELECT ProductID, ProductName, Price FROM Products">
</asp:SqlDataSource>

<asp:GridView 
    ID="GridView1" 
    runat="server" 
    DataSourceID="SqlDataSource1" 
    AutoGenerateColumns="false">
    <Columns>
        <asp:BoundField DataField="ProductID" HeaderText="ID" />
        <asp:BoundField DataField="ProductName" HeaderText="Name" />
        <asp:BoundField DataField="Price" HeaderText="Price" />
    </Columns>
</asp:GridView>
```

##### <span style="color:blue;">9. Difference between DetailsView and FormView.</span>

| DetailsView                                                                                                                                                                           | FormView                                                                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1. Using detailsview we can display, edit, insert or delete a single record from datasource, it can be achieved with the help of boundfield or templatefield.                         | 1. Using FormView we can display, edit, insert or delete a single record, however unlike detailsview, it is only template driven.                                                                                                                      |
| 2. It uses a tabular layout where each field of the record is displayed as a row of its own.                                                                                          | 2. It does not specify a pre-defined layout for displaying the record, instead, you create a template that contains controls to display individual fields from the record.                                                                             |
| 3. Though it can perform edit or delete operations, it is commonly used to display data because of it's tabular layout, it doesn't make good UI to perform edit or delete operations. | 3. It is commonly used to perform update, insert or delete database queries because it allows developers to represent a single field of a record with any control they want. This can help to create more user friendly UI to perform such operations. |
| 4. It is simpler to implement                                                                                                                                                         | 4. It requires more setup.                                                                                                                                                                                                                             |
| 5. It is less flexible than FormView.                                                                                                                                                 | 5. It provides a great flexibility to use controls and data.                                                                                                                                                                                           |
| 6. It can be autogenerated.                                                                                                                                                           | 6. As it is template drive it cannot be autogenerated.                                                                                                                                                                                                 |
##### <span style="color:blue;">10. Difference between DataAdapter and DataReader.</span>

| DataAdapter                                                                                                                                                     | DataReader                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 1. DataAdapter will acts as a Bridge between DataSet and database.                                                                                              | 1. DataReader is used to read the data from the database                                                                               |
| 2. It works with a `DataSet` that can hold multiple tables and relationships, allowing for disconnected data access.                                            | 2. It can direclty read data obtained as a result of select query.                                                                     |
| 3. It used disconnected data access, meaning it access database on demand.                                                                                      | 3. It uses connected data access which means it maintains connection to database.                                                      |
| 4. Supports state management through the `DataSet` or `DataTable`, allowing you to update, delete, or add records, and later push changes back to the database. | 4. Does not support state management, cannot be used to update, delete or insert records in database.                                  |
| 5. With dataadapter we can read any data at any time.                                                                                                           | 5. It is forward read only which means if we have already read one record then we cannot read it again, we can only read next records. |
| 6. Data is retrieved in a batch                                                                                                                                 | 6. Data is read one at a time.                                                                                                         |
| 7. Generally slower than `DataReader` for retrieving data due to its overhead of filling and managing the `DataSet`.                                            | 7. Faster than `DataAdapter` because it has less overhead and works directly with the database connection.                                                                                                                                    |
##### <span style="color:blue;">11. Explain SqlConnection class with an example.</span>
1. The `SqlConnection` class in ASP.NET is part of the `System.Data.SqlClient` namespace and is used to establish a connection to a SQL Server database.
2. A SqlConnection object represents a unique session to a SQL Server data source. With a client/server database system, it is equivalent to a network connection to the server.
3. SqlConnection class object can be used to open or close a connection to database.
4. The constructors of SqlConnection class includes:
	- **SqlConnection():** Initializes a new instance of SqlConnection class
	- **SqlConnection(string):** Initializes a new instance of SqlConnection class with connectionstring passed as argument.
	- **SqlConnection(string, SqlCredential):** Initializes a new instance of the SqlConnection class given a connection string, that does not use `Integrated Security = true` and a SqlCredential object that contains the user ID and password.
5. SqlConnection class object can be used with transaction to ensure data integrity.
6. Example:
```
using System;
using System.Data.SqlClient;

public void FetchData()
{
    string connectionString = "Server=localhost;Database=test;User Id=sa;Password=password;";

    // Create a SqlConnection instance
    using (SqlConnection connection = new SqlConnection(connectionString))
    {
        // Open the connection
        connection.Open();

        // Define the SQL query
        string query = "SELECT Id, Name FROM employees";

        // Create a SqlCommand instance
        using (SqlCommand command = new SqlCommand(query, connection))
        {
            // Execute the command and use a SqlDataReader to read the data
            using (SqlDataReader reader = command.ExecuteReader())
            {
                // Read the data
                while (reader.Read())
                {
                    int id = reader.GetInt32(0); // Assuming the first column is of type int
                    string name = reader.GetString(1); // Assuming the second column is of type string

                    // Output the retrieved data
                    Console.WriteLine($"ID: {id}, Name: {name}");
                }
            }
        }
    } // Connection will be closed automatically here due to 'using' statement
}
```

##### <span style="color:blue;">12. Difference between DataSet and DataReader.</span>

| DataSet                                                                                                     | DataReader                                                                                   |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| 1. Dataset is a disconnected, in-memory representation of data that can hold one or more DataTable objects. | 1. DataReader object provides a way to read data directly from a data source.                |
| 2. It provides disconnected data access.                                                                    | 2. It provides connected data access.                                                        |
| 3. It can be use to perform changes in database.                                                            | 3. It provides read-only access to read data.                                                |
| 4. As it stores the data memory consumption can be high depending on the size of data.                      | 4. It provides low memory consumption as it does not hold the entire dataset in memory.      |
| 5. DataSet is typically slower in performance as compared to DataReader.                                    | 5. DataReader is faster in performance because it is connected, forward only stream of data. |
| 6. DataSet is complex but allows more features such as data relations and constraints.                      | 6. DataReader is much simpler than DataSet and lacks few features.                           |
| 7. We can access any data at any time with dataset.                                                         | 7. It provides forward-only read access, meaning it reads data as one record at a time.      |
##### <span style="color:blue;">13. Write C# code to insert data in database table. Write comments wherever required.</span>
```
using System;
using System.Data;
using System.Data.SqlClient;

class Program
{
    static void Main(string[] args)
    {
        // Define the connection string
        string connectionString = "Server=localhost;Database=empDb;User Id=sa;Password=P@5sw0rD;";

        // Define the SQL query for inserting data
        string insertQuery = "INSERT INTO Employees (Name, Age, Position) VALUES (@Name, @Age, @Position)";

        // Create a new SqlConnection object
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            try
            {
                // Open the connection to the database
                connection.Open();

                // Create a SqlCommand object with the insert query and connection
                using (SqlCommand command = new SqlCommand(insertQuery, connection))
                {
                    // Add parameters to the SqlCommand to prevent SQL injection
                    command.Parameters.AddWithValue("@Name", "John Doe");
                    command.Parameters.AddWithValue("@Age", 30);
                    command.Parameters.AddWithValue("@Position", "Developer");

                    // Execute the insert command
                    int rowsAffected = command.ExecuteNonQuery();

                    // Check how many rows were inserted
                    Console.WriteLine($"{rowsAffected} row(s) inserted.");
                }
            }
            catch (SqlException ex)
            {
                // Handle any SQL exceptions that occur
                Console.WriteLine("SQL Error: " + ex.Message);
            }
            catch (Exception ex)
            {
                // Handle any other exceptions that occur
                Console.WriteLine("Error: " + ex.Message);
            }
        }
    }
}
```

##### <span style="color:blue;">14. What is the use of DataSource control? Explain various data sources in Asp.Net</span>
1. Data source controls that allow you to work with different types of data sources such as a database, an XML file, or a middle-tier business object. Data source controls connect to and retrieve data from a data source and make it available for other controls to bind to, without requiring code.
2. These controls abstract the complexity of data access and allow developers to easily connect to various data sources and manage data-bound controls.
3. Common Uses of DataSource Controls:
	1. **Data Binding**: DataSource controls enable simple data binding for controls like GridView, ListView, and DropDownList.
	2. **CRUD Operations**: They facilitate Create, Read, Update, and Delete operations with minimal code.
	3. **Separation of Concerns**: They help separate the data access logic from the presentation layer.
	4. **Declarative Syntax**: Developers can define data sources in a declarative way using ASP.NET markup.
4. Common DataSource controls in Asp.Net:
	1. **SqlDataSource:** It enables us to work with Microsoft SQL Server, OLE DB, ODBC, or Oracle databases. It allows us to execute SQL commands or stored procedures and bind the results to controls.
	2. **AccessDataSource:** It enables us to work with a Microsoft Access database. It is similar to SqlDataSource.
	3. **ObjectDataSource:** It enables us to work with a business object or other class and create Web applications that rely on middle-tier objects to manage data. It allows binding to custom classes or methods, allowing for more complex data manipulation.
	4. **XmlDataSource:** It enables us to work with an XML file, especially for hierarchical ASP.NET server controls such as the TreeView or Menu control. Supports filtering capabilities using XPath expressions and enables us to apply an XSLT transformation to the data.
	5. **SiteMapDataSource:** It provides access to a site map for navigation purposes. It is used primarily for building menus or breadcrumbs based on the defined site map.
	6. **EntityDataSource:** Simplifies data binding for Entity Framework entities.

##### <span style="color:blue;">15. Write a code to display data from a table named Students(RollNo, Name, Marks) and display on gridview control when page is loaded.</span>
**Web.config**
```
<configuration>
  <connectionStrings>
    <add name="StudentDB" connectionString="Data Source=YourServer;Initial Catalog=YourDatabase;Integrated Security=True" providerName="System.Data.SqlClient"/>
  </connectionStrings>
</configuration>
```
**Students.aspx**
```
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Students.aspx.cs" Inherits="Students" %>

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title>Student Records</title>
</head>
<body>
    <form id="form1" runat="server">
        <div>
            <asp:GridView ID="GridView1" runat="server">
            </asp:GridView>
        </div>
    </form>
</body>
</html>
```
**Students.aspx.cs**
```
using System;
using System.Data;
using System.Data.SqlClient;
using System.Configuration;

public partial class Students : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            BindGridView();
        }
    }

    private void BindGridView()
    {
        string connectionString = ConfigurationManager.ConnectionStrings["StudentDB"].ConnectionString;
        using (SqlConnection conn = new SqlConnection(connectionString))
        {
            string query = "SELECT Name, RollNo, Marks FROM Students";
            using (SqlCommand cmd = new SqlCommand(query, conn))
            {
                SqlDataAdapter da = new SqlDataAdapter(cmd);
                DataTable dt = new DataTable();
                conn.Open();
                da.Fill(dt);
                GridView1.DataSource = dt;
                GridView1.DataBind();
            }
        }
    }
}
```

##### <span style="color:blue;">16. Write any three similarities between formview and detailsview. Explain about item templates in formview.</span>
**Similarities between FormView and DetailsView contro:**
1. Both FormView and DetailsView are data-bound controls in ASP.NET, allowing them to display data from a data source. They can be bound to various types of data sources, such as databases, XML files, or collections.
2. Both controls support multiple modes for displaying data. They can show data in read-only mode, edit mode, and insert mode, making it easy to manage data operations.
3. Both FormView and DetailsView allow the use of templates for customizing the layout of data. Developers can define specific templates for different modes (e.g., item template, edit template) to tailor the appearance and behavior of the controls.
**ItemTemplate for FormView**
1. The ItemTemplate in a FormView control is used to define how the data for each item is displayed when the control is in read-only mode.
2. We can customize the layout and presentation of the data fields within this template.
3. There also exists **EditItemControl** in FormView control that allows to define layout for each item in edit mode.

##### <span style="color:blue;">17. Explain databinding with a dictionary collection.</span>
1. Databinding is a process in which a data source like collection, database, xml etc is bind to data bound controls like gridview, listview etc to display or edit the data.
2. Example:
**Default.aspx**
```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="GridView.Default" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        <div>
            <asp:GridView runat="server" ID="GridView1" AutoGenerateColumns="true">
            </asp:GridView>
        </div>
    </form>
</body>
</html>
```
**Default.aspx.cs**
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace GridView
{
    public partial class Default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            if (!IsPostBack)
            {
                Dictionary<String, int> data = new Dictionary<String, int>
                {
                    { "Gaurav", 22 },
                    { "Saurav", 24 },
                    { "Akshay", 27 }
                };
                GridView1.DataSource = data;
                GridView1.DataBind();
                DetailsView1.DataSource = data;
                DetailsView1.DataBind();
            }
        }
    }
}
```

##### <span style="color:blue;">18. Explain various style properties of GridView control.</span>
1. The `GridView` control in ASP.NET provides several style properties that allow you to customize its appearance.
2. Some of the style properties are:
	1. **GridLines:** Determines the visibility of grid lines in the GridView. It can support values like None, Horizontal, Vertical, Both.
	2. **RowStyle:** This property declaratively defines the style for the data rows in the GridView. This property includes few properties to define the style of each row in gridview:
		1. **BackColor:** Sets the background color of the rows
		2. **ForeColor:** Sets the text color.
		3. **Font:** Defines font settings (size, type)
		4. **CssClass:** Use a css class to each row (tr) element.
		5. **BorderStyle:** Specifies the style of borders.
	3. **HeaderStyle:** Defines the style for the header row of the GridView. This is similar to RowStyle
	4. **FooterStyle:** Specifies the style for the footer row (if enabled) of the GridView. This is similar to RowStyle
	5. **AlternatingRowStyle:** Applies styles to alternate rows in the GridView, which helps improve readability. Styling is quite similar to RowStyle.
	6. **SelectedRowStyle:** Defines the style for the currently selected row. Styling is same as RowStyle.
	7. **EditRowStyle:** Specifies the style for the row that is currently in edit mode. Styling is same as RowStyle.
	8. **EmptyDataRowStyle:** Defines the style for the empty data row when no records are present. Styling is same as RowStyle.
	9. **PagerStyle:** Styles the pager controls (if paging is enabled). Contains the same set of styling properties as defined with RowStyle.

##### <span style="color:blue;">19. Briefly explain following features of GridView control.</span>
**Sorting**
1. The sorting feature of the GridView control in ASP.NET allows users to reorder the rows displayed in the GridView based on the values of a specific column.
2. Sorting can enhance user experience by enabling easier navigation through large datasets.
3. To allow sorting we need to set the AllowSorting property of gridview control to true.
4. Also we need to add the **SortExpression** property for the columns we want to be sortable, the value of SortExpression property is simply the name of the field to sort.
5. Once done with this we need to implement sorting event handler, the event handler needs to be implemented in code behind file and the event handler name should be provided as value to **OnSorting** property of gridview control.

**Paging**
1. The paging feature of the GridView control in ASP.NET allows you to manage large sets of data by dividing them into manageable pages.
2. This improves performance and user experience by displaying only a subset of data at a time.
3. To enable paging, we need to set the `AllowPaging` property of the GridView to `true` and specify the number of records to display per page using the `PageSize` property.
4. We need to handle the `PageIndexChanging` event to update the current page index when the user interacts with the paging controls.
5. When paging is enabled, an additional row called the pager row is automatically displayed in the GridView control. The pager row contains controls that allow the user to navigate to the other pages. You can control the settings of the pager row (such as the pager display mode, the number of page links to display at a time, and the pager control's text labels) by using the PagerSettings property.
