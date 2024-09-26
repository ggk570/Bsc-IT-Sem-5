#### <span style="color:blue;">1. Explain exception handling mechanism in C#.</span>
1. An exception is defined as an event that occurs during the execution of a program that is unexpected by the program code.  The actions to be performed in case of occurrence of an exception is not known to the program.
2. In such cases we can use exception handling to handle runtime errors in a controlled manner, allowing your program to continue operating or to terminate gracefully. It helps in managing unexpected situations, ensuring that errors do not cause the application to crash unexpectedly.
3. In C# an exception is represented by an object representing an error or an unexpected event that occurs during program execution.
4. Exceptions are derived from System.Exception class in C#. There are several common exceptions such as:
	- **System.SystemException:** It is base class for system exceptions like **IndexOutOfRangeException** and **NullReferenceException**.
	- **System.ApplicationException:** It is base class for application-specific exceptions, though it's generally recommended to derive your custom exceptions from `Exception` directly
5. We can create our own exception by deriving a class from System.Exception class. This class would then required a constructor to represent our custom exception. To throw this exception we have to use **throw** keyword wherever applicable.
6. Exceptions are handled using **try-catch-finally block**.
7. The code that might throw an exception goes inside the try block. Catch block catches and handles the exception thrown inside the try block. If we want then we can have multiple catch blocks to handle different types of exceptions. If we are unsure about the exception type, we can specify the base class Exception object. The code inside the finally block is always executed regardless of exception is thrown or not. It is typically used for cleanup code such as closing file streams or database connections.
8. If we have used try block, then we need to use at least one catch block or we will get compilation error. The finally block is optional.
9. General Syntax:
```
try{
//Code that might throw an exception
}
catch(ExceptionType1 ex){
//Code to handle ExceptionType1 exception
}
catch(ExceptionType2 ex){
//Code to handle ExceptionType2 exception
}
catch(Exception ex){
//Code to handle any type of exception. If exceptiontype1 or exceptiontype2 occurs then it will be handled by above catch statements, if any other exception occurs then it will be handled by this block
}
finally{
//Code that will always be executed - optional
}
```
8. Example:
```
using System;
public class Program{
	public static void Main(String[] Args){
		try{
			int[] numbers = {1,2,3};
			Console.WriteLine(numbers[10]);
		}
		catch(IndexOutOfRangeException ex){
			Console.WriteLine("An index was out of range : " + ex.Message);
		}
		catch(Exception ex){
			Console.WriteLine("An unexpected error occured " + ex.Message);
		}
		finally{
			Console.WriteLine("Finally block");
		}
	}
}
```

#### <span style="color:blue;">2. Enumerate and ellaborate on the different file types accessible within an ASP.Net Application.</span>
1. In an ASP.NET application, various file types are used to manage different aspects of the application. Each type of file serves a specific purpose, contributing to the application's functionality, configuration, and presentation.
2. Below is the list of file types in ASP.Net:
	1. **.aspx:** Represents the UI (user interface) of the application in ASP.NET Web Forms. It contains HTML markup and server-side controls.
	2. **.aspx.cs/.aspx.vb**: This represents code behind files which contains backend code (server side logic) to manage the application. These files are specific to their corresponding .aspx file.
	3. **.ascx:** These files contains user controls that represents User Interface. They contain reusable piece of UI which can be included in one or more .aspx file. These files can also have their code behind files like .**ascx.cs**.
	4. **.asax:** The Global.asax file, also known as the ASP.NET application file, is an optional file that contains code for responding to application-level and session-level events raised by ASP.NET
	5. **Web.config:** These files stores configuration for the asp.net. It contains configuration settings like connection strings, custom application settings, and authentication settings.
	6. **.js:** Javascript files for client-side scripting code that runs in browser.
	7. **.css:** Defines styles and layout of web pages for front end code.
	8. **.dll:** Dynamic link libraries, contains the compiled code that can be used by application or other applications. These are usually placed in bin folder.

#### <span style="color:blue;">3. What is view state? Give advantages and disadvantages of view state.</span>
1. View State is used to store user data on page at the time of post back of web page. It does not hold the controls, it holds the values of controls.
2. **View State** is a mechanism that allows the state of server-side controls to be preserved across postbacks. Essentially, it helps in maintaining the values of controls and other data between server round-trips.
3. The View State is stored in a hidden field on the page and is sent back and forth between the client and server during postbacks.
4. When a page is loaded for the first time, the values of the controls are initialize with the default value, the view state hidden field contains this default values in serialize format.
5. When the user interacts with the controls and changes data, e.g select an item in a dropdown list and then click on submit button. The data is submitted to server, on the server side the user updated data is then serialized and stored in viewstate field and then it is transferred to client as response. This helps to maintain the state of controls across postbacks.
**Advantages of View State:**
1. View State ensures that the state of server-side controls is maintained across postbacks. This is particularly useful for maintaining form data, user input, and control settings
2. Developers do not need to manually manage the state of controls. The View State automatically handles the state management, simplifying development.
3. It provides a consistent user experience by preserving the state of the page and controls, making it easy to implement features like multi-step forms.
4. Since the state is managed on the client side, there's no need for server-side state management solutions, which can reduce server load.
**Disadvantages of View State:**
1. View State data is stored in a hidden field on the page, which increases the page's size. Large View State can lead to slower page load times and increased bandwidth usage.
2. For large pages with extensive View State, the serialization and deserialization process can impact performance. This is especially noticeable on slower connections or with complex pages.
3. Although View State data is encoded and optionally encrypted, it can still be a security risk if sensitive data is included. Improper handling of View State can lead to data exposure or tampering.
4. Debugging issues related to View State can be complex, as the state information is serialized into a string format and can be difficult to interpret.
5. Since View State is stored on the client side, any tampering or manipulation by the client can potentially lead to security issues, even though ASP.NET provides mechanisms to mitigate these risks.

#### <span style="color:blue;">4. Provide a concise overview of application events.</span>
1. In ASP.NET, application events are a set of events that occur during the lifecycle of an application, allowing you to execute code at specific points.
2. Basic ASP.NET features such as session state and authentication use application events to plug into the ASP.NET processing pipeline.
3. Global.asax allows us to write event handlers that react to global events in web applications. Global.asax files are never called directly by the user, rather they are called automatically in response to application events.
4. These events are crucial for managing application-wide settings and handling requests. Here’s a concise overview:
	1. **Application_Start:** Triggered when the application first starts. Use this event to initialize application-wide settings, such as configuring routes or setting up application-level services.
	2. **Application_End**: Occurs when the application is shut down or stopped. This is where you can clean up resources or log information about the application’s shutdown.
	3. **Application_BeginRequest**: Fired at the beginning of each request. Useful for tasks such as logging request details or performing actions before the request is processed.
	4. **Application_EndRequest**: Triggered at the end of each request, after the response has been sent to the client.
	5. **Session_Start:** This event is fired when new user visits the application website.
	6. **Session_End:** This event is fired when user's session expires or they leave application website.
	7. **Application_Error:** This occurs in response to an unhandled error.

#### <span style="color:blue;">5. Explain ListBox control with properties and methods</span>
1. ListBox is a control used to display a list with some items on a web page. Not only it displays the list but it also allows users to select an item from this list and submit the data in postback request.
2. The items in this list are provided using ListItem control.
3. ListBox is created by using below syntax:
```
<asp:ListBox runat="server" ID="ListBox1">
<asp:ListItem>Item 1</asp:ListItem>
<asp:ListItem>Item 2</asp:ListItem>
<asp:ListItem>Item 3</asp:ListItem>
</asp:ListBox>
```
4. **Properties of ListBox:**
	1. **SelectedValue:** Gets the value of the selected item from ListBox.
	2. **SelectedIndex:** Gets the value of selected index from ListBox.
	3. **SelectedItem:** Gets the text of selected item from ListBox.
	4. **Items:** Gets the collection of Items in ListBox, it is of **ListItemCollection** Type.
	5. **SelectionMode:** It can be Single or Multiple, if single the user can select only one item, it multiple user can select multiple items.
	6. **SelectedItems:** If selectionmode is multiple, this property returns a collection of selected items. 
	7. **DataSource:** Use to assign a datasource (any object containing data like database, xml files, list, arrays or collection of custom objects)
	8. **DataTextField:** Name of the data source field to supply text of items. Generally this field came from datasource.
	9. **DataValueField:** Name of the data source field to supply values of the items.
5. **Methods of ListBox:**
	1. **ListBox1.Items.Add(value):** Used to add an item to the list.
	2. **ListBox1.Items.Remove(value):** Used to remove an item from the list.
	3. **ListBox1.Items.Clear():** Used to clear the list.
	4. **ListBox1.Items.FindByText(text):** Search for an item with specified text.
	5. **ListBox1.Items.FindByValue(value):** Search for an item with specified value.
	6. **ListBox1.DataBind():** Binds the listbox to its datasource, updating the items based on datasource, datatextfield and datavaluefield properties.

#### <span style="color:blue;">6. Write Short note on adrotator and calendar control.</span>
**AdRotator:**
1. AdRotator control is used in asp.net to display advertisement banner on a web page.
2. AdRotator controls can be used to display a rotating series of advertisements or images on a web page. It allows us to present different images or content in a slide-show format, providing a dynamic and visually engaging way to showcase content.
3. Typically it uses an XML file to define the advertisements. The XML file contains a list of image URLs, alternate texts, and hyperlinks.
4. It can automatically rotates through the images or advertisements based on the specified intervals.
5. Example:
	1. Define an xml file (ads.xml):
	```
	<?xml version="1.0" encoding="utf-8" ?>
	<Advertisements>
	  <Ad>
		    <ImageUrl>~/images/ad1.jpg</ImageUrl>
		    <NavigateUrl>http://www.example.com</NavigateUrl>
		    <AlternateText>Example Ad 1</AlternateText>
	  </Ad>
	  <Ad>
	    <ImageUrl>~/images/ad2.jpg</ImageUrl>
	    <NavigateUrl>http://www.example.com</NavigateUrl>
	    <AlternateText>Example Ad 2</AlternateText>
	  </Ad>
	</Advertisements>
	```
	2. Add AdRotator control to our .aspx web page:
	```
	<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="Default" %> 
	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml">
	<head runat="server">
		<title>AdRotator Example</title>
	</head>
	<body>
		<form id="form1" runat="server">
			<div>
				<asp:AdRotator ID="AdRotator1" runat="server" AdvertisementFile="~/Ads.xml" Width="300px" Height="250px" />
			</div>
		</form>
	</body>
	</html>
	```
	1. Build the website and navigate to the page with adrotator control.
**Calendar Control:**
1. The **Calendar** control in ASP.NET is used to display a calendar on a web page. It allows users to select dates or view dates across different months and years.
2. It can be useful for date-based inputs, scheduling, or event management.
3. Calendar control provides properties and methods to customize the appearance of the calendar to provide a more user friendly view.
4. To add a calendar control to a web form:
```
<asp:Calendar ID="Calendar1" runat="server" 
	  ShowTitle="true" 
	  SelectionMode="Day" 
	  OnSelectionChanged="Calendar1_SelectionChanged" />
```
5. The above code will trigger an event, when a date is changed or selected by the user, to handle the event we can create an event handler function in code behind file.
```
protected void Calendar1_SelectionChanged(object sender, EventArgs e)
{
    DateTime selectedDate = Calendar1.SelectedDate;
    // Handle the selected date
    Response.Write("Selected Date: " + selectedDate.ToShortDateString());
}
```

#### <span style="color:blue;">7. What is range validator? Describe any four properties of it.</span>
1. The **RangeValidator** control in ASP.NET is used to validate that a user’s input falls within a specified range of values.
2. It is commonly used in web forms to ensure that numeric inputs, dates, or other data types fall within a certain range, helping to enforce data integrity and improve user experience.
3. Asp server controls by default don't allow values to be accepted in particular range, the developer has to manually write code for it. E.g An input field where a user can specify age, but the user can insert any values age like -45 which is invalid. RangeValidator control will save the developer to write few lines of validation code instead it does all the task in few steps.
4. **Properties of RangeValidator:**
	1. **ControlToValidate**: Specifies the ID of the input control that the validator will validate. For example, it could be a `TextBox` where the user enters data.
	2. **Type**: Specifies the data type of the input to be validated. Common types include `Integer`, `Double`, `Date`, and `String`. This determines how the `MinimumValue` and `MaximumValue` are interpreted.
	3. **MinimumValue**: Defines the minimum acceptable value for the input. The type of the value (e.g., integer, date) depends on the `Type` property.
	4. **MaximumValue**: Defines the maximum acceptable value for the input. Like `MinimumValue`, it is dependent on the `Type`.
	5. **ErrorMessage**: The message displayed to the user when the input fails validation. This helps inform users about what went wrong and how to correct it.
	6. **EnableClientScript**: Indicates whether client-side script is used to perform the validation. If set to `true`, the validation is performed on the client side before the form is submitted, providing faster feedback to the user.
	7. **ValidationGroup**: Allows grouping of multiple validation controls. Only controls within the same validation group are validated together. This is useful when you have multiple forms on the same page.
5. Example:
```
<asp:TextBox ID="txtAge" runat="server" />
<asp:RangeValidator ID="RangeValidator1" 
                    runat="server" 
                    ControlToValidate="txtAge"
                    MinimumValue="18"
                    MaximumValue="65"
                    Type="Integer"
                    ErrorMessage="Age must be between 18 and 65."
                    EnableClientScript="true" />
```

#### <span style="color:blue;">8. Write a short note on asp.net page lifecycle.</span>
1. When an ASP.NET page runs, the page goes through a life cycle in which it performs a series of processing steps. These include initialization, instantiating controls, restoring and maintaining state, running event handler code, and rendering.
2. If we as a developer develop custom controls we need to be familiar with page life cycle in order to correctly initialize controls, populate properties with view state data and run control behaviour code.
3. The following points discuss about various stages of asp.net page lifecycle:
	1. **Page Request:** The page request occurs before the page life cycle begins. When the page is requested by a user, ASP.NET determines whether the page needs to be parsed and compiled (therefore beginning the life of a page), or whether a cached version of the page can be sent in response without running the page.
	2. **Start:** In the start stage, page properties such as [Request](https://msdn.microsoft.com/en-us/library/xc67sd5e(v=vs.100)) and [Response](https://msdn.microsoft.com/en-us/library/3tbxeb64(v=vs.100)) are set. At this stage, the page also determines whether the request is a postback or a new request and sets the [IsPostBack](https://msdn.microsoft.com/en-us/library/5zabsw0t(v=vs.100)) property. The page also sets the [UICulture](https://msdn.microsoft.com/en-us/library/ey25safb(v=vs.100)) property.
	3. **Initialization:** At this stage, the page and its controls are initialized. Each control's `OnInit` method is called, allowing you to set up properties and initialize controls. A master page and themes are also applied to the page if applicable.
	4. **Load:** During load, if the current request is a postback, control properties are loaded with information recovered from view state and control state.
	5. **Postback Event Handling:** If the request is a postback, event handlers for controls are executed. This is where you handle user interactions such as button clicks and form submissions.
	6. **Rendering:** The `Render` method is called for each control, generating the HTML markup that will be sent to the client's browser. This is where the final output of the page is created. Just before calling the Render method, view state is saved for the page and all controls.
	7. **Unload:** After the page has been fully rendered and sent to the client, the `Unload` event occurs. This is where you can clean up resources and perform any final operations before the page is discarded.

#### <span style="color:blue;">9. What is meant by validation of data. How to use Asp.Net validation control to validate user input?</span>
1. **Data validation** is the process of ensuring that user input is accurate, complete, and within expected ranges before it is processed or stored.
2. This is crucial for maintaining data integrity, improving user experience, and protecting against security threats such as SQL injection and cross-site scripting (XSS).
3. Validation controls can be of two type:
	1. **Client side:** This type of validation is perform inside client browser with the help of scripting languages like JavaScript. Client side validation provides more user friendly features and are performance efficient as they don't put load on server. However these controls can be bypassed, hence for security purpose these are not the preferred mechanism. However it can be combined with server side validation to mitigate security risks.
	2. **Server side:** This is done in the backend i.e on server. In asp.net we can achieve this by using C#. This type has some performance issue because user data is submitted to server then validated and after these steps response is sent to client. Server side validation is helpful for placing a barrier to hackers.
4. ASP.NET provides several types of validation controls that can be used to validate user input in web forms. Some of the common validation controls are:
	1. **RequiredFieldValidator:** Ensures that user does not leave a field empyt.
	2. **CompareValidator:** Compares the value of one input control to another (e.g., ensuring a password and confirm password match).
	3. **RangeValidator:** Validates that input lies in a specified range.
	4. **RegularExpressionValidator**: Validates input against a regular expression (useful for formats like email addresses).
	5. **CustomValidator**: Allows for custom validation logic defined in code-behind.
	6. **ValidationSummary**: Displays a summary of all validation errors.
5. By default these validation controls work on both client side and server side.
6. Example
**WebForm1.aspx**
```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Practice.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        <div>
            <asp:Label ID="Label1" runat="server">Name:</asp:Label>
            <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
            <asp:RequiredFieldValidator ControlToValidate="TextBox1" ID="RequiredFieldValidator1" runat="server" ErrorMessage="Name is Required"></asp:RequiredFieldValidator>
            <br /><br />
            <asp:Label ID="Label2" runat="server">Age:</asp:Label>
            <asp:TextBox ID="TextBox2" runat="server"></asp:TextBox>
            <asp:RangeValidator ControlToValidate="TextBox2" ID="RangeValidator1" runat="server" MinimumValue="18" MaximumValue="25" ErrorMessage="Age must be between 18 and 25"></asp:RangeValidator>
            <br /><br />
            <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
        </div>
    </form>
</body>
</html>
```
**WebForm1.aspx.cs**
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace Practice
{
    public partial class WebForm1 : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
        }
        protected void Button1_Click(object sender, EventArgs e)
        {
            if (Page.IsValid) //Checks if page fullfills validation requirements
            {
                Response.Write($" Hello {TextBox1.Text} of age {TextBox2.Text}");
            }
        }
    }
}
```
**Web.config**
```
<appSettings>
	//Add below line in appSettings of Web.config to avoid jquery errors
	<add key="ValidationSettings:UnobtrusiveValidationMode" value="None" />
</appSettings>
```

#### <span style="color:blue;">10. Explain any two Site Navigation Controls in asp.net</span>
1. In ASP.Net site navigation feature provides a consistent way for users to navigate our site. As our site grows, and as we move pages around in the site, it can become difficult to manage all of the links. ASP.NET site navigation enables us to store links to all of our pages in a central location, and render those links in lists or navigation menus on each page by including a specific Web server control.
2. Site maps are XML files which are mainly used to describe the logical structure of the web application. It defines the layout of all pages in web application and how they relate to each other. Whenever you want you can add or remove pages to your site map there by managing navigation of website efficiently. Site map files are defined with .sitemap extension. `<sitemap>` element is the root node of the sitemap file.
3. Below are a list of Site Navigation Controls used in asp.net:
	1. **SiteMapPath:** This control obtains navigation data from sitemap file. This data includes information about the pages in your Web site, such as the URL, title, description, and location in the navigation hierarchy. Storing navigation data in one place makes it easier to add and remove items in the navigational menus of a Web site.
	`<asp:SiteMapPath ID="SiteMapPath1" runat="server" />`
	2. **Menu:** Creates a menu for navigating through a site, usually shown as a horizontal or vertical list of links. We can add individual menu items to the control by specifying them in the [Items](https://msdn.microsoft.com/en-us/library/4yw0e4fw(v=vs.100)) property. The [Items](https://msdn.microsoft.com/en-us/library/4yw0e4fw(v=vs.100)) property is a collection of [MenuItem](https://msdn.microsoft.com/en-us/library/7as0bse6(v=vs.100)) objects.
	```
	<asp:Menu ID="Menu1" runat="server" Orientation="Horizontal">
    <Items>
        <asp:MenuItem Text="Home" NavigateUrl="~/Default.aspx" />
        <asp:MenuItem Text="Products">
            <asp:MenuItem Text="Category 1" NavigateUrl="~/Category1.aspx" />
            <asp:MenuItem Text="Category 2" NavigateUrl="~/Category2.aspx" />
        </asp:MenuItem>
    </Items>
	</asp:Menu>
	```

#### <span style="color:blue;">11. What is postback? Explain IsPostBack property with suitable example.</span>
1. In ASP.NET, **postback** refers to the process where a web page sends data back to the server for processing. This typically occurs when a user interacts with controls on the page, such as buttons or dropdowns, which triggers a server-side event, causing the page to reload.
2. It's a round trip between the browser and the server, and back to the browser.
3. The `IsPostBack` property is a Boolean property of the `Page` class that indicates whether the page is being loaded in response to a postback or if it is being loaded for the first time.
4. Typically IsPostBack property is used in backend in Page_Load event to differentiate between the first request and postback request and accordingly take action using conditional statements.
5. Example:
**Default.aspx**
```
<% Page language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="Default" %>
<! DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
	<title>PostBack Example</title>
</head>
<body>
	<form ID="form1" runat="server">
	<div>
		<asp:Label ID="Label1" runat="server" Text="Name:"></asp:Label>
		<asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
		<br /><br />
		<asp:Button ID="Button1" runat="server" Text="Submit" />
	</div>
	</form>
</body>
</html>
```
**Default.aspx.cs**
```
using System;
public partial class Default : System.Web.UI.Page{
	protected void Page_Load(object sender, EventArgs E){
		if(IsPostBack){
			Response.Write($"Hello {TextBox1.Name}");
		}
	}
}
```

#### <span style="color:blue;">12. What is an event? How is an event handler added.</span>
1. An event is a message sent by an object to signal the occurrence of an action. The action can be caused by user interaction, such as a button click, or it can result from some other program logic, such as changing a property's value. The object that raises the event is called the _event sender_.
2. The event sender doesn't know which object or method will receive (handle) the events it raises. The event is typically a member of the event sender; for example, the [Click](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.button.click#system-web-ui-webcontrols-button-click) event is a member of the [Button](https://learn.microsoft.com/en-us/dotnet/api/system.web.ui.webcontrols.button) class, and the [PropertyChanged](https://learn.microsoft.com/en-us/dotnet/api/system.componentmodel.inotifypropertychanged.propertychanged#system-componentmodel-inotifypropertychanged-propertychanged) event is a member of the class that implements the [INotifyPropertyChanged](https://learn.microsoft.com/en-us/dotnet/api/system.componentmodel.inotifypropertychanged) interface.
3. Events allow developers to define specific responses to user interactions, enhancing interactivity and functionality within web applications.
4. Event handlers are methods that define what happens when an event occurs. An event handler responds to the event by executing the code within it.
5. To add an event handler we have to create a method that matches the signature of the event.
6. After creating a method we have to attach our method to the event, so that whenever the event occurs our method is called.

#### <span style="color:blue;">13. Write a short note on list controls in asp.net.</span>
1. In ASP.NET, **list controls** are used to display a collection of items to users, allowing them to select one or multiple options
2. These controls enhance user interaction by providing a structured way to present choices.
3. Some of most commonly used list controls in asp.net are:
	1. **DropDownList:** It displays single item from a dropdown list, users can select one option from list, which expands upon clicking
	2. **ListBox:** Displays a list of items that can be selected, allowing for multiple selections if the `SelectionMode` property is set accordingly, users can see all availabe options at once.
	3. **RadioButtonList:** A list of radio buttons where only one option can be selected at a time. Suitable for scenarios where users must choose a single option from multiple choices.
	4. **CheckBoxList:** Similar to the `RadioButtonList`, but allows users to select multiple options. Useful for situations where multiple choices are permitted.
4. To define items inside this list control we need to use **ListItem** control, a single ListItem control represents one single item in the list.
5. ListControls also supports various events like OnSelectIndexChanged which represents that a user selected an option from the list.
6. ListControls also has properties to retrieve user selected items as well as to create list items from a datasource.
7. Example
```
<asp:DropDownList ID="ddlCountries" runat="server">
    <asp:ListItem Text="USA" Value="1"></asp:ListItem>
    <asp:ListItem Text="Canada" Value="2"></asp:ListItem>
</asp:DropDownList>

```

#### <span style="color:blue;">14. Explain the need of User Control. How it is created and used.</span>
1. A user control is a kind of composite control that works much like an ASP.NET Web page—you can add existing Web server controls and markup to a user control, and define properties and methods for the control. You can then embed them in ASP.NET Web pages, where they act as a unit.
2. User controls are similar to a normal asp.net page, however the server controls and other html goes in .ascx file and the codebehind file is .cs file. The usercontrol page is not directly accessible as other .aspx page. The usercontrols are used as a component in other pages to create User Interface.
3. **Need of User Controls:**
	1. **Reusability:** They allow developers to create components that can be reused across different pages, reducing duplication of code and speeding up development.
	2. **Encapsulation:** User controls encapsulate functionality and UI elements, which helps in managing complex applications by breaking them down into smaller, manageable pieces.
	3. **Consistency:** - They help maintain a consistent user interface throughout the application. If a design change is needed, updating the user control updates it everywhere it’s used.
	4. **Simplified Development:** User controls streamline the development process by providing pre-built functionality that can be integrated easily.
	5. **Easier Maintenance:** Bugs and updates can be addressed in one place, which then propagates to all instances of the control, simplifying ongoing maintenance.
4. **Creation of UserControls:**
	1. Right click on the project in Visual Studio and click on 
		Add Item > New Item
	2. Choose **Web User Control** (ASCX) and give it a name (e.g., `LoginControl.ascx`).
	3. In the `.ascx` file, define the HTML structure and ASP.NET controls. For example:
	```
	<%@ Control Language="C#" AutoEventWireup="true" CodeBehind="LoginControl.ascx.cs" Inherits="YourNamespace.LoginControl" %>
	<div>
    <asp:TextBox ID="txtUsername" runat="server" Placeholder="Username" />
    <asp:TextBox ID="txtPassword" runat="server" TextMode="Password" Placeholder="Password" />
    <asp:Button ID="Button1" runat="server" Text="Login" OnClick="Button1_Click" />
	</div>
	```
	3. Add Logic in the Code Behind File:	In the associated code-behind file (e.g., `LoginControl.ascx.cs`), implement the logic for events, like handling the login:
	```
	using System;
	namespace YourNamespace
	{
	    public partial class LoginControl : System.Web.UI.UserControl
	    {
		    public String Username
		    {
			    get { return txtUsername.Text; }
		    }
		    public String Password
		    {
			    get { return txtPassword.Text; }
		    }
	        protected void btnLogin_Click(object sender, EventArgs e)
	        {
	            // Handle login logic here
	        }
	    }
	}
	```
5. **Usage of UserControl:**
	1. Include the user control in a page (.aspx)
	`<%@ Register TagPrefix="uc" TagName="LoginControl" Src="~/LoginControl.ascx"%>`
	2. Add the user control to the page
	`<uc:LoginControl ID="LoginControl1" runat="server" />`
	3. Access the properties and events in code behind file of .aspx page
	```
	protected void Page_Load(Object sender, EventArgs e)
	{
		string username = LoginControl1.Username;
	}
	```

#### <span style="color:blue;">15. What are .aspx files? Explain code behind class in detail.</span>
1. **.aspx files** are ASP.NET web page files that contain markup, which typically includes HTML, CSS, and server-side controls. They are used to create dynamic web pages in ASP.NET applications.
2. When a user requests an .aspx page, the ASP.NET engine processes the page and generates HTML that is sent to the client’s browser.
3. Key Features of .aspx Files:
	1. **Server-Side Processing**: .aspx files can contain server-side code written in languages like C# or VB.NET, which allows for dynamic content generation based on user interactions or data from a database.
	2. **Markup**: They use a combination of HTML and ASP.NET server controls. Server controls are prefixed with `<asp:`, allowing the ASP.NET framework to handle their processing.
	3. **Page Lifecycle**: Each .aspx page has a defined lifecycle, which includes events such as `Page_Load`, `Page_Init`, and `Page_PreRender`. Developers can hook into these events to execute code at specific points in the page's lifecycle.
**CodeBehind File:**
1. The **code-behind class** is a C# or VB.NET class file that contains the server-side logic for an .aspx page. It is where you implement the behavior and functionality of the page, separating the presentation layer (markup in .aspx) from the business logic (code in the code-behind).
2. Key Components of Code-Behind:
	1. **File Naming**: The code-behind file usually has the same name as the .aspx file, but with a .aspx.cs or .aspx.vb extension. For example, if you have `MyPage.aspx`, the code-behind file will be `MyPage.aspx.cs` (for C#) or `MyPage.aspx.vb` (for VB.NET).
	2. **Inherits Attribute**: In the .aspx file, the `Inherits` attribute in the `@Page` directive links the markup to its corresponding code-behind class.
	3. **Class Definition**: The code-behind file contains a class definition that inherits from `System.Web.UI.Page`.
	4. **Event Handlers**: Commonly, you will define event handlers for page lifecycle events and control events (like button clicks).
	5. **Control Interaction**: You can interact with server controls defined in the .aspx file directly in the code-behind by using their IDs.
	6. **Accessing Data**: Code-behind classes often contain logic for accessing databases, processing user input, and managing session state.
	7. **Data Binding**: You can bind data to controls (like GridView, DropDownList) in the code-behind.

#### <span style="color:blue;">16. Explain each of the following in brief.</span>
 **Web Forms**
1. ASP.NET Web Forms is a programming model that lets you create web applications and websites using the ASP.NET framework.
2. Web Forms are web pages built on the ASP.NET Technology. It executes on the server and generates output to the browser. It is compatible to any browser to any language supported by .NET common language runtime. It is flexible and allows us to create and add custom controls.
3. We can use Visual Studio to create ASP.NET Web Forms. It is an IDE (Integrated Development Environment) that allows us to drag and drop server controls to the web forms. It also allows us to set properties, events and methods for the controls. To write business logic, we can choose any .NET language like: Visual Basic or Visual C#.
4. Web Forms are made up of two components: the visual portion (the ASPX file), and the code behind the form, which resides in a separate class file.
 
 **Page Rendering**
1. Page rendering in ASP.NET refers to the process of converting server-side code and markup into HTML that is sent to the client's browser. This is a crucial part of the ASP.NET Web Forms page lifecycle.
2. Page rendering is a part of page life cycle.
3. The rendering process specifically involves the following steps:
	1. PreRender Event:
		Just before rendering, the `PreRender` event occurs. This is where you can make final adjustments to control properties. It’s the last opportunity to modify control values before they are converted into HTML.
	2. Rendering Controls:
		Each control in the page, including server controls (like `GridView`, `Button`, etc.), has a `Render` method that is responsible for outputting HTML. This method generates the appropriate HTML markup for the control based on its properties and state
	3. Html Output:
		The output from the `Render` methods of all controls is collected and combined into a single HTML string. This string represents the complete page content.
	4. Sending Response:
		Once the HTML content is generated, it is sent back to the client’s browser as an HTTP response. The browser then interprets this HTML and renders it as a visual web page.

**Page Load Event**
1. The **Page Load event** is a crucial part of the ASP.NET page lifecycle. It is triggered every time a page is requested, whether it's the first time or a postback (when the page is sent back to the server for processing). It’s commonly used for initializing controls, setting default values, or loading data from a database.
2. The Page Load event handler has a specific signature and is usually defined as follows:
	`protected void Page_Load(object sender, EventArgs e){ }`
3. We can define our own logic within the Page Load event handler to manipulate controls, set values, or perform operations based on the page's state.
4. The Page Load event is where you can determine if the page is being loaded for the first time or as a result of a postback. This is done using the `IsPostBack` property.

**Page PreRender Event**
1. The **PreRender event** is an important stage in the ASP.NET page lifecycle that occurs just before the page is rendered to the client. This event is useful for making final adjustments to the page and its controls before the HTML is generated and sent to the browser.
2. The PreRender event handler is defined with a specific signature similar to other page events:
`protected void Page_PreRender(object sender, EventArgs e){ }`
3. The PreRender event occurs after the Page Load event but before the rendering phase. This means that all controls have been loaded and any user interactions (like postbacks) have been processed.
4. You can make any last-minute changes to the properties of controls (e.g., setting visibility, updating text) that need to reflect the final state of the page.
5. If you need to add or modify controls dynamically based on user input or application state, the PreRender event is the right place to do it.

#### <span style="color:blue;">17. List any four category of server control. Explain common properties of web server controls.</span>
**Html Server Controls:**
HTML server controls are standard HTML elements that have been enhanced to work with server-side code. They allow you to create simple, lightweight web pages with HTML markup while still leveraging the capabilities of ASP.NET. They are defined with **runat="server"** attribute.
E.g input, form, div, span
**Web Server Controls:**
Web server controls are ASP.NET-specific controls that provide rich functionality and built-in features. They are more complex than HTML server controls and come with properties, methods, and events. They are define with **<asp:** tag
E.g button, label, textbox
`<asp:Label runat="server" ID="Label1"></asp:Label>`
**Data Controls:**
Data controls are specialized server controls designed for displaying and manipulating data from data sources such as databases, XML files, or collections. They provide data binding capabilities and are ideal for building data-driven applications.
E.g GridView, FormView, DataList, SqlDataSource
**Validation Controls:**
Validation controls are used to validate user input on web forms. They help ensure that the data submitted by users meets specific criteria before processing it.
E.g RequiredFieldValidator, RangeValidator
**Rich Controls:**
In addition to the preceding controls, the ASP.NET page framework provides a few, task-specific controls called rich controls. Rich controls are built with multiple HTML elements and contain rich functionality. Examples of rich controls are the Calendar control and the AdRotator control.

#### <span style="color:blue;">18. Explain anatomy of a webform.</span>
1. A web form in ASP.NET is a key component for creating interactive web applications. It allows users to input data, which can then be processed by the server.
2. Web form is comprised of few key elements:
	1. **Page Directive:**
		The page directive is a crucial part of any ASP.NET web form. It provides metadata about the page, including its language, code-behind file, and inheritance.
	2. **Html Structure:**
		A web form typically includes standard HTML elements. This structure forms the skeleton of the page, including the `<html>`, `<head>`, and `<body>` tags.
	3. **Form Tag:**
		The `<form>` tag is essential in a web form. In ASP.NET, it has the `runat="server"` attribute, which allows server-side processing.
	4. **Server Controls:**
		Server controls are the interactive elements within the form. These can include various types of input fields, buttons, and data display controls. Each control has properties, methods, and events.
	5. **CodeBehind File:**
		The code-behind file contains the server-side logic for the web form. This is where event handlers are defined, and data processing occurs. The file typically has a `.aspx.cs` or `.aspx.vb` extension.

#### <span style="color:blue;">19. Brief about Graphics class and it's any 5 methods.</span>
1. The **Graphics** class in .NET is part of the `System.Drawing.dll` assembly and is used for drawing on various surfaces, such as forms, images, and controls. It provides methods to draw shapes, text, and images, making it a fundamental component for creating graphics in Windows applications.
2. Graphics classes are System.Drawing, System.Text, System.Printing, System.Internal, System.imaging, System.Drawing2D and System.Design name spaces.
3. The Graphics class encapsulates Graphics Device interface drawing surfaces. Before drawing any object we have to create surface using Graphics class
4. **Properties:**
	- **DpiX and DpiY:** Get the horizontal and vertical dots per inch (DPI) of the graphics object, which indicates the resolution of the graphics.
	- **Clip:** Gets or sets the clipping region of the graphics object.
	- **Transform:** Gets or sets the transformation matrix for the graphics object.
5. **Methods:**
	- **DrawLine:** Draws a line connecting two points.
	`graphics.DrawLine(Pens.Black, startPoint, endPoint);`
	- **DrawRectangle:** Draws a rectangle defined by a `Rectangle` structure.
	`graphics.DrawRectangle(Pens.Red, new Rectangle(10, 10, 100, 50));`
	- **FillRectangle:** Fills the interior of a rectangle with a brush.
	`graphics.FillRectangle(Brushes.Blue, new Rectangle(10, 10, 100, 50));`
	- **DrawString:** Draws the specified text string at the specified location using a specified font and brush.
	`graphics.DrawString("Hello, World!", new Font("Arial", 12), Brushes.Black, new PointF(10, 10));`
	- **DrawImage:** Draws an image from an `Image` object at the specified location.
	`graphics.DrawImage(image, new Point(0, 0));`
	- **Clear:** Clears the entire drawing surface and fills it with the specified color.
	`graphics.Clear(Color.White);`
	
