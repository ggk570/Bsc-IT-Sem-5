#### <span style="color:blue;">1. Draw and explain .Net Framework Architecture.</span>
![](https://github.com/ggk570/Bsc-IT-Sem-4/blob/main/AWP/Solved%20Papers/Screenshots/net_framework_architecture.jpg)
1. The .net framework is a software development framework created by Microsoft. Using .net framework anyone can create desktop, mobile or web applications. .Net provide support of multiple programming languages like C#, F#, C++, python, VB, etc.
2. Components of .Net Framework includes:
- Common Language Runtime (CLR):
		CLR provides runtime environment to execute .Net Framework programs. When an application in run CLR loads required libraries and compile the code into native machine language, besides this it performs automatic memory management, exception handling.
- Class Libraries:
		.Net Framework provides huge class libraries which is a collection of classes, interfaces, and value types. These class libraries provides a foundation to .Net Programming. This libraries provides a large set of prebuilt functions to create a range of application. The library includes a variety of namespaces that provides access to classes that provide features such as file I/O, networking, database access and graphical user interface design.
- Common Type System (CTS):
		Common Type System or CTS defines how types are declared, used and managed in .Net Framework. Since .Net Framework consists of different programming lanugages, each programming language have it's own set of data types and it's own way to declare, used and manage them. To bring the data types of all these languages under one umbrella CTS lays the foundation. This helps in interoperatibility of different languages.
- Common Language Specification (CLS):
		CLS defines a set of rules and guidelines that all .Net Framework languages must follow for the purpose of interoperatibility.
- Microsoft Intermediate Language (MSIL):
		When a .net framework program is first compiled, it is not directly compiled into native machine code (which is dependent on cpu architecture and os), instead it is compiled into an intermediate language which is platform independent. When this MSIL code is executed the it is converted into native machine code by just in time compiler which is a part of CLR.
- Assemblies:
		Assemblies are compiled code libraries used by .Net applications, they can be dlls or exes and contain metadata code and resources.

#### <span style="color:blue;">2. How does garbage collector function in context of .net. Provide a brief overview of the Base Class Library in .Net</span>
**Garbage Collector:**
1. The .Net framework's garbage collector is a component of CLR, it is used to automatically manage memory allocation and deallocation to improve performance of the program and prevent memory leaks.
2. Garbage collector uses a **mark and sweep** algorithm to identify and reclaim unused memory.
   The GC identifies which identifies which objects are still reachable (in use) and mark them as reachable, it then reclaims the memory used by objects that are not marked.
3. After collecting garbage, the GC compacts the memory to reduce fragmentation and improve memory allocation efficieny, this process moves live objects together making free contagious memory for allocation.
4. Before reclaiming memory, the GC calls the finalizers of objects that require cleanup. Finalizers are special methods used to release resources like file handles or database connections.
**Base Class Library:**
1. Base Class Library is a fundamental component of .Net Framework, it is a repository of classes, interfaces and value types that forms foundation for .Net Applications.
2. The BCL provides basic functionalities like input/output operation, string operation, basic data types, exception handling etc.
3. The BCL includes core namespaces like System, Sytem.Collections, System.IO, Sytem.Text etc.
4. The BCL form the foundation upon which more specialized functionality can be implementated by using inheritance.
5. The core of the .Net framework lies in BCL.

#### <span style="color:blue;">3. Explain any five properties/methods of Array Class.</span>
**An Array** is a data structure that can hold group of elements of same data type. In .Net Framework, Array class is the fundamental class that provides methods and properties to work with arrays.
**Properties**
1. **Length:**
		Returns number of elements in one dimensional array or total number of elements in a multidimensional array.
		`int[] num = {1,2,3};`
		`Console.WriteLine(num.Length); //3`
2. **Rank:**
		Returns number of dimension of an array, for example 2 dimensional array will have rank 2
		`int[,] num = new int[2,3];`
		`Console.WriteLine(num.Rank);`
3. **IsFixedSize:**
		Returns a boolean value, true if size of the array is fixed
4. **IsReadOnly:**
		Returns a boolean value, true if array is read only.
5. **IsSynchronized:**
		Gets a value indicating whether access to the array is synchronized or not i.e thread safe or not.
**Methods**
1. **GetValue:**
		Returns the value of an element in an array at a specified index. The method comes in different overloaded forms to retrieve value of elements in multidimensional arrays.
		`int[] num = {1,2,3};`
		`Console.WriteLine(num.GetValue(1));`
2. **SetValue:**
		Used to set value of an element at a specified index in an array. Similar to GetValue method it comes in different overloaded form to support multidimensional array.
		`int[] num = {1,2,3};`
		`Console.WriteLine(num.SetValue(2,4));`
3. **LastIndexOf:**
		It is a static method earches for the specified object and returns the index of last occurence of that particular object.
		`int[] num = {1,2,34,56,1,4};`
		`Console.WriteLine(Array.LastIndexOf(num, 1));`
4. **BinarySearch:**
		It is a static method which searches for an element in a sorted array using binary search algorithm, if the element is found then the index of element is return or else -1 is returned.
		`int[] num = {1,2,3,4,5,6};`
		`Console.WriteLine(Array.BinarySearch(num, 2));`
5. **ForEach:**
		Static method version of foreach loop that works with Array Class, it takes an array object as the first parameter and a function as other parameter, it then calls the function for each element in the array.
		`int[] num = {1,2,3,4,5,6};`
		`Array.ForEach(num, Console.WriteLine);`

#### <span style="color:blue;">4. Explain the process of data type conversion in C# and identify its various types.</span>
1. Data type conversion is a process in which data of a particular type is converted into another type for various operations. Since data type defines the structure to store data in memory and also it defines the amount of memory required to store data. It is important for a programmer to know about data types and its conversion process to effectively write programs.
2. There are two basic types of data type conversion in C#:
	- **Implicit Conversion:**
		In this type of conversion, the compiler automatically converts data of one type into another. This automatic conversion is performed by the compiler when there is no risk of loss of data. This usually happens when data type which can hold small size of data is converted into data type which can hold large size of data. Think of it as transferring water from a small bucket into a large bucket.
		`int num = 13;`
		`double num1 = num;`
	- **Explicit Conversion:**
		In this type conversion method, the data type conversion needs to be explicity specified by the programmer. Explicit conversion is done with the help of cast operator.  Here is a risk of data loss due to overflow. Think of this as transferring water from a large bucket into a small bucket. If the large bucket contains water that the small bucket can hold then there is no issue but if the large bucket is fulled then some amount of water would be lost due to overflow, same happens with data. The largest positive number an int can hold is **2^31 -1** but if a double with just one number greater than this, is converted into int the data would be lost and the final value will be smallest int which is **-2^31**.
		`double num = 1234;`
		`Console.WriteLine((int) num);`
3. Other than these basic type of conversion, C# provides a **Convert** class to convert data of one base type into another base type. The base type supported by Conver class are:
	**Boolean, Char, SByte, Int16, Int32, Int64, UInt16, UInt32, UInt64, Single, Double, Decimal, DateTime and String.**
4. Convert class provides static methods to convert one base type into other base type. These methods can handle complex type conversion scenarios. E.g converting string to an int.
	`String num = "123";`
	`int converted = Convert.ToInt32(num);`

#### <span style="color:blue;">5. How to derive new class from base class. Give one example.</span>
1. In C# to derive a new class from a base class, we need to create new class inhereting the base class. Inhereting a base class allows us to extend features of the base class without need to touch the pre-existing code. This saves us from getting unwanted bugs. We can also override any existing methods of the base class in our new class, this allows us to use the existing feature along with required changes.
2. To create class that inherits another class we must follow a syntax, we have to use **:** in front of our new class name and then we need to specify the name of the class from which our new class is being derived.
3. Example
```
using System;
public Class Animal{
	public string Name {get; set;}
	public Animal(String name){
		Name = name;
	}
	public void Eat(){
		Console.WriteLine($"{Name} is eating!");
	}
	// Virtual Method can be overridden in child class
	public virtual void MakeSound(){
		Console.WriteLine($"{Name} makes a sound");
	}
}
public Class Dog: Animal{
	public Dog(String name) : base(name){}
	public override MakeSound(){
		Console.WriteLine($"{Name} barks!!");
	}
	public void play(){
		Console.WriteLine($"{Name} is playing with a ball!");
	}
}
public class Program{
	public static void Main(){
		Animal animal = new Animal("Generic Animal");
		animal.Eat();
		animal.MakeSound();
		Dog pluto = new Dog("pluto");
		dog.eat();
		dog.MakeSound();
		dog.play();
	}
}
```

#### <span style="color:blue;">6. What steps are involved in constructing a fundamental class in C#. Please delineate different class modifiers.</span>
1. C# is an object oriented programming language, every functional and non functional aspect of the program goes inside the class. Class is a template or blueprint that defines the structure, behaviour and attributes of an object.
2. Behaviour is defined by methods in a class, when an of object of a class is created and these methods are called, they execute some functionality which represents a behavious. Similarly these object will have properties defined inside the class. We can change the values of these properties by accessing the objects and it's methods, these properties together represents the state of the object.
3. To create a class in C#, we must follow few steps:
	- It's an optional step, we can first create a namespace using namespace keyword followed by namespace name and pair of curly braces {}. The class definition goes inside this curly braces. Namespaces are used to organized classes.
	- We need to declare the class with an access specifier and Class keyword followed by the class name which is followed by curly braces {}.
	- We can then define the class members which can include properties, methods and constructors inside this curly braces {}.
	E.g
	```
	namespace myclass{
		public class Bike{
			public int mileagePerLitre;
			public int topSpeed;
			private String engineNo {get; set;}
			private int speedKmPerHr = 0;
			public void accelerate(){
				if(speed < topSpeed)
					speed += 1;
			}
			public void engineBreak(){
				if(speed > 0)
					speed -= 1;
			}
			public void break(){
				speed = 0;
			}
		}
	}
	```
**Class Modifiers:**
1. Access modifiers in C# are **used to specify the scope of accessibility of a member of a class or type of the class itself**. For example, a public class is accessible to everyone without any restrictions, while an internal class may be accessible to the assembly only
2. In C# there are 6 types of access modifiers:
		1. **public:**
		The type or member can be accessed by any other code in the same assembly or another assembly that references it.
		2. **private:**
		The type or member can be accessed only by code in same class, it cannot be accessed by object or it cannot be derived by any class.
		3. **protected:**
		The type or member can be accessed only by the code in the same class or in a class that is derived from that class. These members cannot be directly accessed by objects but they can accessed by derived classes in the same assembly or different assembly.
		4. **internal:**
		The type or member can be accessed by any code in the same assembly but not from other assembly. Classes or members of classes declared as internal can only be accessible through the same assembly (.dll or .exe file). With this access specifier a member can be accessed by the object in the same assembly, it can also be accessed by derived classed in the same assembly.
		5 **protected internal:**
		The type or member can be accessed by any code in the assembly in which it’s declared, or from within a derived class in another assembly. It is a combination of protected and internal. The protected internal access modifier seems to be a confusing but is a union of protected and internal in terms of providing access but not restricting.
		6. **private protected:**
		The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.

#### <span style="color:blue;">7. Explain foreach loop with suitable example.</span>
1. The foreach loop is used to iterate over a collection of items, such as arrays, lists or other enumerable collections. It simplifies the process of looping through each item without needing to use an index variable.
2. Unlike the for loop we don't need to use an index variable, boolean conditions and increment/decrement operators, we can directly iterate over the collection by following the proper syntax.
3. Foreach loop saves us from the overhead of using boolean conditions like we do with while and for loops. With foreach loop we just have to create a variable that represents data type of data in a collection or other iterable item. It makes use of **in** operator to iterate over a collection.
4. The basic syntax for foreach loop:
```
foreach(var item in collection){
	//Statements to be executed
}
```

5. Example:
```
string[] stringArray = {"one", "two", "three"};
foreach(string item in stringArray){
	Console.WriteLine(item);
}
```
6. With the above example when the clr encounters a foreach loop, it declares the variable **item** and assigns it value of first element in the **stringArray**, after executing the code inside the curly braces, the loop startsover with second element of the array and this goes on until the array is fully traversed.
7. The limitation of foreach loop is that it is readonly, for example with for loops we can traverse the array by using an index number and at the same time using the index number we can manipulate the array, however since foreach loop stores the element of the array in a separate variable we cannot manipulate data in an array.

#### <span style="color:blue;">8. Distinguish between interface and abstract classes.</span>

| Interface                                                                                                                                                     | Abstract Class                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| 1. Interfaces are declared using interface keyword. E.g interface MyInterface{}                                                                               | 1. Abstract classes are like other classes and are declared using abstract keyword. E.g abstract class MyClass{} |
| 2. Interfaces can contain only declaration of methods, properties, events or indexers. Since C# 8, default implementations can also be included in interfave. | 2. It can contains both implementation and declaration parts.                                                    |
| 3. It cannot contain a constructor                                                                                                                            | 3. It can contain a constructor.                                                                                 |
| 4. It does not contain static members                                                                                                                         | 4. It can contain static members.                                                                                |
| 5. It can only contain public access modifier but is never specified while declaring members.                                                                 | 5. It can contain different access modifiers type like public, private, protected etc.                           |
| 6. It's purpose is to implement peripheral abilities of class.                                                                                                | 6. It's purpose it create more abstracted version of a class.                                                    |
| 7. A class can use multiple interface.                                                                                                                        | 7. A class can use only one abstract class.                                                                      |
| 8. All methods in an interface are abstracted by default but the abstract keyword is never used.                                                              | 8. At least one method should be abstract method and should be specified using abstract keyword.                 |
#### <span style="color:blue;">9. What is a namespace. Describe system namespace.</span>
1. Namespace is a way to orgranize and group related classes, interfaces etc.
2. It helps to control the scope of methods and classes in larger .Net programming projects
3. Namespace helps to avoid naming conflicts, e.g if we declare a class in one namespace, we can declare another class with the same name in another namespace.
4. To define a namespace in C#, we will use the namespace keyword followed by the name of the namespace and curly braces containing the body of namespace:
```
namespace MyNamespace{
	//Classes
	//Interfaces
	//Structures
	//Nested-Namespace
}
```
5. Members of a namespace are accessed by a dot (**.**) operator
6. To use a class from a particular namespace, we can use the fully qualified name of the class
	`E.g MyClass obj = new MyNamespace.MyClass();`
	or we can include the namespace with a **using** directive:
	`E.g using Mynamespace;`
7. The **System** namespace is one of the fundamental namespaces in .NET and C#. It provides classes and types that are fundamental to the .NET Framework. This namespace includes a wide range of functionality including basic data types, collections, and utilities.
8. The System namespace includes basic data types which includes Int32, double, String, Boolean etc.
9. System namespace also provides classes for various types of collections such as **List`<T>`**, **Dictionary`<TKey, TValue>`** and **Queue`<T>`**. 
10. Other than this it includes classes for various Input/Output operations, threading purposes, string manipulation and much more.

#### <span style="color:blue;">10. What is an assembly. Explain the difference between public and private assembly.</span>
1. An assembly is a collection of types and resources that are built to work together and form a logical unit of functionality.
2. Assemblies take the form of executable (.exe) or dynamic linking library (.dll) files and are the building block of .Net Framework Applications.
3. They provide the common language runtime with the information it needs to be aware of type implementations.
4. Key Concepts of Assemblies:
	1. **Manifest:** Contains metadata about the assembly such as its version, culture and the list of type it contains. The manifest also includes information about other assemblies that the current assembly depends on.
	2. **Metadata**: Information about the types, methods, and other elements contained in the assembly. This allows the .NET runtime to understand the assembly's contents and how to interact with them.
	3. **Code**: The compiled C# (or other .NET language) code that performs the assembly's functionality.
	4. **Resources**: Additional files that the assembly might need, such as images, data files, etc.
	5. **Type Information**: Defines the classes, interfaces, and other types contained in the assembly, along with their members.
5. **Public Assembly:**
	- These are designed to be shared across multiple applications. Public assemblies are often part of a library or framework that provides common functionality to various applications.
	- These are typically installed in Global Assembly Cache which is a machine wide store used to manage shared assemblies.
	- Public assemblies usually have strong names, which include the assembly’s name, version, culture, and public key token. This strong naming ensures that the correct version of the assembly is used by applications.
	- E.g System.data.dll and System.Xml.dll
6. **Private Assembly:**
	- These assemblies are used by a single application.
	- Suppose we have a project in which we refer to a DLL so when we build that project that DLL will be copied to the bin folder of our project.
	- That DLL becomes a private assembly within our project. Generally, the DLLs that are meant for a specific project are private assemblies.
	- Private assemblies do not need to be strongly named and can be versioned according to the application's needs. They are typically not versioned to the same degree of formality as public assemblies.
	- E.g A utility library or custom component that is used exclusively by a specific application.

#### <span style="color:blue;">11. Write a simple C# program to demonstrate class, object and method call. Use comments wherever required.</span>
1. A class is a blueprint or template that defines methods and properites for a specific type of object. These methods and properties are to be used by object. In some cases there are static methods and properties that don't required an instance instead they are directly called or accessed by the class itself.
2. An object is an instance of the class that resides in heap. Consider an example of car, car is generic name for anything that has 4 wheels, moves with the help of engine, has features like AC. Now this can be represented by a generic class name car which defines properties like nameOfCar, noOfWheels = 4, mileage, topSpeed and methods accelerate(), break() which increases the speed of car and stop the car. However the car class on it's own doesn't represent anything rather than a blueprint, so there need to be specific version of this. Here we can create an object of car class and specify values to the properties. Thus this object will represent a real world object.
3. Since the properties defines the characteristics of the object, thus they represent the state of object and the methods do something with the objects or properties of the object, they represents the behaviour.
4. A sample program:
```
using system

namespace{
	public class Car{
		//Defines name of the car
		public String name;
		//Defines mileage of car in km/ltr
		public int mileage;
		//Defines top speed in km/hr
		public int topSpeed;
		//Defines speed of the car in km/hr, default is 0
		public int speed = 0;
		//EngineNo of car, as it represent unique identity
		private String engineNo {get; set;}

		//Method to accelerate car
		public void accelerate(){
		//Test if car is already running at top speed or not
			if(speed < topSpeed)
				speed += 2;
		}
		public void brake(){
			speed = 0;
		}
	}
	public class Program{
		public static void main(String[] args){
			//Create an object of Car class
			Car myCar = new Car();
			
			//Assign values to properties to represent real world object
			myCar.name = "Tarzan";
			myCar.topSpeed = 200;
			myCar.mileage = 8;
			myCar.engineNo = "ABC123";
		
			//Check the initial speed of the car
			Console.WriteLine(myCar.speed);
			//Call the accelerate method to increase the speed of the car
			myCar.accelerate();
			//Again check the speed of myCar to see if accelerate method properly
			//worked or not
			Console.WriteLine(myCar.speed);
		}
	}
}
```

#### <span style="color:blue;">12. Explain compiling and execution of C# program.</span>
1. Compiling is a process in which their is a conversion of source code in programming language to machine language which can be understood and executed by the machine.
2. For C# language there is a slight difference in compilation and execution process.
3. When we write our code in C# using ide like visual studio and then build our program, our code gets compiled into Microsoft Intermediate Language (MSIL) by C# Compiler (csc).
4. There are various steps performed by the CSC in this stage:
	- Lexical Analysis: Breaking down the code into tokens.
	- Syntax Analysis: Parsing the tokens to build a syntax tree.
	- Semantic Analysis: Checking for semantic errors and ensuring that the code follows C# rules.
	- Code Generation: Generating IL code from the syntax tree.
5. If there is any syntax or semantic error in our code the compiler will show an error and the compilation would fail. If there are no errors, IL code would be generated in form of assembly which is .dll or .exe file depending on our project.
6. The assembly contains metadata which provides information to CLR to understand the IL code and interact with it.
7. When the assembly is executed, Just In Time compiler (component of CLR) converts the IL code to native machine language that process could execute.
8. During the execution CLR provides various services such as garbage collection and exception handling. It manages the execution of program and provides runtime environment that ensures the program was run as intended.

##### <span style="color:blue;">13. What is the difference between value type and reference type in C#.</span>

| Value Type                                                                                                                                        | Reference Type                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. A value type is a type which can hold the data directly in memory.                                                                             | 1. A reference type is a type which holds a reference (memory address) to the actual data.                                                                                                                              |
| 2. Value Types are stored in stack.                                                                                                               | 2. Reference Types are stored in heap.                                                                                                                                                                                  |
| 3. When we assign one value type variable to another, the value is copied. Each variable has it's own copy of data.                               | 3. When we assign one reference type variable to another, both variables will refer to the same object on the heap. Modifying the object through one reference will affect the object as seen through other references. |
| 4. Value types are generally more efficient for small, frequently accessed data because they don’t require heap allocation or garbage collection. | 4. Reference types can incur overhead due to heap allocation and garbage collection. They are usually used for larger, more complex data structures and objects.                                                        |
| 5. In C# value types cannot be null unless they are declared as nullable.                                                                         | 5. In C# reference types default to null if not explicitly initialized.                                                                                                                                                 |
| 6. E.g int, float, double, char, bool                                                                                                             | 6. E.g String, object, arrays.                                                                                                                                                                                          |
#### <span style="color:blue;">14. Explain inheritance along with its type.</span>
1. Inheritance is a fundamental concept in object-oriented programming (OOP) that allows a class (known as the derived or child class) to inherit properties and methods from another class (known as the base or parent class). This promotes code reuse and establishes a hierarchical relationship between classes.
2. The derived class can then extend or override these members to provide specific behavior.
3. In C# there are several types of inheritance:
	- **Single Inheritance:**
		This happens when a class is derived from only one single class.
	- **Multi-Level Inheritance:**
		In this type of inheritance, class is derived from another class which is itself derived from another class. E.g Class C inherits Class B and Class B inherits Class A. So here Class C indirectly inherits properties and behavious of Class A.
	- **Multiple Inheritance:**
		In this inheritance a class is created from more than one base class. This inheritance is not directly supported by .Net programming languages like C#. A class in C# cannot directly inherit from multiple classes, however it can implement multiple interfaces. E.g class C implements interface A and B.
	- **Hierarchial Inheritance:**
		In this inheritance more than one dervied classes are created from one base class and further child classes are created from these derived classes forming an hierarchy. E.g class A has two child classes B and C. Now class B has child classes D and E, class C has child classes F and G.
	- **Hybrid Inheritance:**
		This is combination of two or more type of inheritance. Although C# does not support hybrid inheritance directly with classes (due to restrictions on multiple inheritance), it can be achieved using a combination of class inheritance and interface implementation.
		E.g class C inherits class B which further inherits class A - Multi-Level Inheritance.
		class C implements interface D. Thus class C is a combination of Multi-Level Inheritance and Multiple Inheritance.

#### <span style="color:blue;">15. What is an ArrayList, state it's method and properties.</span>
1. An `ArrayList` in C# is a class that belongs to the `System.Collections` namespace. It represents a non-generic collection of objects that can be accessed by index.
2. ArrayList can store elements of any type and it can dynamically resize itself as elements are added or removed.
3. Properties:
	- **Count:**
		Returns the number of elements in an ArrayList object.
	- **IsReadOnly:**
		Returns a boolean value indicating whether the ArrayList is read-only. For ArrayList this is always False.
	- **IsFixedSize:**
		Returns a boolean value indicating whether arraylist has fixed size or not. For arraylist this is always False.
	- **Capacity:**
		Gets or sets the number of elements that the ArrayList can contain.
	- **IsSynchronized:**
		Gets a value indicating whether access to ArrayList is synchronized (thread safe).
4. Methods:
	- **Add(Object Value):**
		Adds an object to end of the arraylist.
	- **Clear():**
		Removes all elements from the ArrayList.
	- **Contains(Object Value):**
		Returns true if an element is present in arraylist or else false.
	- **IndexOf(Object Value):**
		Returns the zero-based index of first occurence of specific object in the ArrayList.
	- **Insert(int index, Object Value):**
		Inserts an element at a specified index in the arraylist.
	- **Remove(Object Value):**
		Removes first occurence of specified object from the ArrayList.
	- **RemoveAt(int index):**
		Removes element at the specified index.
	- **Sort():**
		Sorts the elements in the ArrayList using default comparer.
	- **ToArray():**
		Copies the ArrayList elements to a new **Object** array.
	- **CopyTo(Array array, int index):**
		Copies the entire arraylist in one dimensional array at the specified array index

##### <span style="color:blue;">16. What are .Net Languages. Explain various features of C#.</span>
1. .Net Programming Languages are programming languages that are designed to run on the .Net Framework. They are supported by CLR which provides run time environment for executing code and managing various aspects such as memory management and exception handling.
2. .Net programming languages includes:
	1. C#
	2. F#
	3. VB .Net
	4. JScript
	5. Python
3. Features of C#:
	1. C# is a general purpose versatile language developed by Microsoft widely used for a variety of applications from desktop software to web apps.
	2. C# is an object orient programming languages, hence supports concepts of classes, interfaces, inheritance, polymorphism, encapsulation etc. This provide a modern and more better approach for creating applications.
	3. C# is statically typed which means type of variable or expression is known at compile time. This means type checking is performed at compile time preventing any runtime errors and performance issues.
	4. C# is strongly type which means it strictly enforces type rules for performing operations on data and avoiding unintended type conversions and operations.
	5. Since C# is a .Net Programming Language it is supported by CLR, thus it provides automatic memory management for storage efficiency.
	6. It is capable of interoperatibility with other .Net Programming Languages.
	7. C# also supports multithreading to run multiple threads concurrently thereby improving performance of code execution.

#### <span style="color:blue;">17. What is property. Explain read-write property with proper syntax and example.</span>
1. In C#, a **property** is a member of a class that provides a mechanism to read, write, or compute the value of a private field. Properties are a way to encapsulate data and control access to it, providing a more controlled way to interact with the class's internal state compared to using public fields directly.
2. A property typically consists of:
	- **Getter:** A method (or accessor) that returns the value of the property.
	- **Setter:** A method (or mutator) that sets the value of a property.
3. Here is a basic syntax for defining a property in C#:
```
<access_modifier> <return_type> <property_name>{
	get { //body }
	set { //body }
}
```
4. In the above syntax instead of //body we can place our code. This allows us the flexibility to control what happens when a code outside the class tries to access a private field value or tries to change data of private field. Thus properties help us in access control.
5. It is not necessary to always use getters and setters, we can only use getters to provide read access or we can only use setters to provide write access.
6. If in a property we define both getters and setters than this grants a **Read-Write** access to private field.
7. In C# we can simplify property declarations using auto implemented properties where the compiler automatically creates a private field for us. Syntax for auto-implemented properties:
```
public class MyClass{
	public String Name {get; set;}
}
```
8. Example:
```
namespace Students{
	public class Student{
		// Private Field no outside code could access or change value
		private int marks;
		// Property
		public int Marks{
			get { return marks; }
			set { marks = value; }
		}
	}
	public class Program{
		public static void Main(String[] args){
			Student ravi = new Student();
			ravi.Marks = 95;
			Console.WriteLine(ravi.Marks);
		}
	}
}
```

#### <span style="color:blue;">18. Explain one dimensional and two dimensional arrays with proper example.</span>
1. An array is data structure which can hold multiple elements of same data type.
2. When a variable is declared as array then the variable can contain fixed number of elements of same data type. The number of elements to be contained should be defined at the time of declaration.
3. **One dimensional array:** It is the simplest form of array, this type of array does not contain any array or collection as it's element. It has single rows and n number of columns. The elements can be accessed by single index.
4. **Two dimensional array:** It is an array of arrays. It is often used to represent matrices. It has rows and columns. Elements can be accessed using two indices.
5. Example:
```
namespace Example{
	public class MyClass{
		public static void Main(String[] args){
			int size = 5;
			// One Dimensional Array
			int[] evenNo = new int[size];
			for(int i = 0; i < size; i++){
				evenNo[i] = 2*(i + 1) ;
			}
			for(int i = 0; i < size; i++){
				Console.WriteLine(evenNo[i]);
			}
			
			// Two Dimensional Array
			int[,] matrix = new int[3,3];
			matrix[0,0] = 1;
			matrix[0,1] = 2;
			matrix[0,1] = 3;
			matrix[1,0] = 4;
			matrix[1,1] = 5;
			matrix[1,2] = 6;
			matrix[2,0] = 7;
			matrix[2,1] = 8;
			matrix[2,2] = 9;
			for(int i = 0; i < 3; i++){
				for(int j = 0; j < 3; j++){
					Console.WriteLine(matrix[i][j]);
				}
			}
		}
	}
}
```

#### <span style="color:blue;">19. List various reference types in C#. Also explain boxing operation with example.</span>
1. Variables of Reference Types stores reference to data which means reference type variable stores memory address where actual data resides and not the data.
2. Reference type includes:
	- **Classes:** It is a blueprint for creating objects, it defines field, properties, methods and events.
	- **Interfaces:** An interface defines a contract that classes can implement. It contains method signatures and properties but no implementation
	- **Delegates:** A delegate is a type that represents reference to methods with a specific signature, these are used for callback methods and event handling.
	- **Arrays:** These are collections of elements of same type. They can be one dimensional or multi dimensional.
	- **Strings:** Strings are immutable sequences of characters, these are also considered as reference type though they behave as value type.
	- **Objects:** Object is an alias for **System.Object** in .Net. In the unified type system of C#, all types, predined and user defined inherit indirectly or directly from System.Object. These object types are also reference type.
3. **Boxing Operation:**
	1. Boxing is a process of converting a value type like int, char, float etc to an object or to any other type that dervies from System.Object. This involves wrapping the value type in a reference type so it can be treated as an object.
	2. Boxing involves allocating memory on heap.
	3. Unboxing is reverse process which involves converting an object back to value type.
	4. Example:
	```
	using System;
	public class Program{
		public static void Main(String[] args){
			int number = 123;
			//Boxing convert value type to object type
			//obj will hold reference to boxed number
			object obj = number;
			
			//Unboxing convert object type back to value type
			//obj is cast back to an integer
			int unboxedNumber = (int) obj;
			Console.WriteLine("Original Value : " + number);
			Console.WriteLine("Unboxed Value : " + unboxedNumber);
		}
	}
	```

#### <span style="color:blue;">20. Elaborate array memory representation with an example.</span>
1. Array is a data structure that holds elements of same type in a continuous block of memory.
2. An array is of fixed sized i.e it only contains a fix number of elements and it can contain elements of same type, the size and type of element is defined at the time of declaration.
3. The memory assignment is done using a simple calculation, consider an array of 5 int, since int requires 4 byte, 5 int would require (5x4) bytes i.e 20 bytes.
4. The first element would be store in a base address, the remaining elements would then be stored in next continuous blocks of memory. If the base address starts from 0x10000000, the next addresses would be 0x10000001, 0x10000002, 0x10000003, 0x10000004.
5. Example
```
using System;
using System.Runtime.InteropServices;

class Program
{
    static void Main()
    {
        // Array
        int[] numbers = { 10, 20, 30, 40, 50 };

        // Pin the array in memory so it doesn't get moved by the garbage collector
        GCHandle handle = GCHandle.Alloc(numbers, GCHandleType.Pinned);
        IntPtr baseAddress = (IntPtr)handle.AddrOfPinnedObject();
        Console.WriteLine(baseAddress);

        // Accessing and displaying each element
        for (int i = 0; i < numbers.Length; i++)
        {
            Console.WriteLine($"Element at index {i}: {numbers[i]}");
			Console.WriteLine($"Address for index {i}: {baseAddress+ 1}");
            baseAddress = (IntPtr)baseAddress+1;
        }
    }
}
```

#### <span style="color:blue;">21. Explain any 5 properties/methods of Math Class.</span>
1. The Math Class in C# provides a collection of Static Methods and Constants for performing mathematical operations.
2. Below is a list of common properties and methods of Math Class:
	1. **Math.Abs(Value):**
		Returns absolute value of a specified number. It returns positive magnitude of a number, regardless of its sign.
		`Console.WriteLine(Math.Abs(-13));`
	2. **Math.Max(x, y):**
		Returns larger of two specified numbers. It helps in finding maximum number between two numbers.
		`Console.WriteLine(Math.Max(12, 13));`
	3. **Math.Min(x, y);**
		It is used to find lowest number between two provided values.
		`Console.WriteLine(Math.Min(5,9));`
	4. **Math.Sqrt(value):**
		Returns square root of a specified number. E.g Math.Sqrt(16) will return 4
		`Console.WriteLine(Math.Sqrt(16));`
	5. **Math.Round(value):**
		Rounds a number to nearest whole number
		`Console.WriteLine(9.99);`
	6. **Math.Pow(base, exponent):**
		This is used for exponentiation. It returns a number raised to specified power.
		`Console.WriteLine(Math.Pow(2,3));`
	7. **Math.Sin(value):**
		Returns sine value for a given angle, similarly we have cos, tan etc.
	8. **Math.Log(value):**
		Returns natural (base e) logarithm of specified number.
	9. **Math.Log10(value):**
		Returns base 10 logarithm of a specified number.
3. Below is a list of constants:
	1. **Math.PI:**
		Represents pi (3.14159)
	2. **Math.E:**
		Represents the base of natural logarithm, also known as Euler's number.
	3. **Math.Tau:**
		Represents mathematical constant tau, which is 2xPI, it is sometimes used instead of PI in circle related calculations.

#### <span style="color:blue;">21. Explain static members and partial class.</span>
**Static Members:**
1. Static members in C# are associated with the type itself instead of the instance.
2. We can define class members as static using the static keyword. When we declare a member of a class as static, it means no matter how many objects of the class are created, there is only one copy of the static member.
3. **Static Fields:**
	A static field is shared among all instances of a class. It is initialized only once, when the class is first instantiated. Static fields are used to store data that is common to all instances of a class. For example, you might use a static field to keep track of the number of instances created.
4. **Static Properties:**
	A static property is similar to a static field but includes encapsulation. Static properties are useful for exposing global or shared data in a controlled manner.
5.  **Static Methods:**
	A static method is a method that belongs to the class itself rather than to any specific object. It can only access other static members of the class. Static methods are used for operations that are independent of instance data.
6. **Static Constructors:**
	When a constructor is defined with static keyword then it becomes static constructor, a static constructor is used to initialize any static data, or to perform a particular action that needs to be performed only once. It's called automatically before the first instance is created or any static members are referenced. A static constructor is called at most once.
**Partial Classes:**
1. **Partial classes** allow you to split the definition of a class across multiple files. This can be particularly useful for managing large classes, separating auto-generated code from user-written code, or organizing code for better maintainability.
2. All parts of a partial class must have the same class name and be declared with the `partial` keyword. The compiler combines them into a single class.
3. We can separate different aspects of the class into different files. For example, we might separate methods and properties from the class’s event handlers.
4. Partial classes are often used to separate auto-generated code (such as code generated by designers or tools) from user-written code. This helps in keeping the auto-generated code untouched and more manageable.
5. Partial methods are methods defined in a partial class that are optional. They allow us to define a method signature in one part of the class and implement it in another part.
#### <span style="color:blue;">22. Explain static constructor and copy constructor with examples.</span>
**Static Constructor:**
1. A **static constructor** is a special constructor in C# that initializes static members of a class. It is called automatically by the runtime before any static members of the class are accessed or any static methods are called or when the first instance of the class is created.
2. Static constructors have same name as class, they cannot have parameters and they are defined without any access modifier.
3. Example:
```
public class Logger{
	private static String logfilepath;
	static Logger(){
		logfilepath = "logfile.txt";
		Console.WriteLine("Static Constructor Called.");
	}
	public static void Log(string message){
		Console.WriteLine($"Logging message to {logfilepath}");
	}
}
public class Program{
	public static void Main(String[] Args){
		//Static constructor would be automatically called
		Logger.Log("Error 404");
	}
}
```
**Copy Constructor:**
1. A **copy constructor** is a constructor that initializes a new object as a copy of an existing object. This allows you to create a new object with the same values as another object.
2. Copy constructors are helpful because if we directly assign an object variable to another object like we do with base type, we will end up having two references to same object instead of a copy. 
3. Copy constructors have same name as the class and they are defined with public access modifier.
4. Example
```
Using System;
public class Person{
	public String Name {get; set;}
	public int Age {get; set;}
	//default constructor
	public Person(){}
	//Copy constructor
	public Person(Person p){
		Name = p.Name;
		Age = p.Age;
	}
}
public class Program{
	public static void Main(String[] Args){
		Person p1 = new Person();
		p1.Name = "Varun";
		p1.Age = 25;
		Person p2 = new Person(p1);
		Console.WriteLine(p2.Name);
		Console.WriteLine(p2.Age);
	}
}
```

#### <span style="color:blue;">23. What is delegates. Explain multicast delegates with an example.</span>
1. In C#, delegates are types that can hold references to methods with matching signatures
2. Delegates are similar to function pointers in C and C++, but they are more secure and type-safe. They are often used to implement callbacks and events
3. The first step when using a delegate is to define its signature. The signature is a combination of several pieces of information about a method: its return type, the number of parameters it has, and the data type of each parameter.
4. A delegate variable can point only to a method that matches its specific signature. In other words, the method must have the same return type, the same number of parameters, and the same data type for each parameter as the delegate.
5. General syntax of delegate is:
	`access_modifier delegate return_type delegate_name([parameters_list])`
6. Example:
```
public class Program
{
    public delegate void Notify(string message);

    public static void ShowMessage(string message)
    {
        Console.WriteLine(message);
    }

    public static void Main()
    {
        Notify notify = new Notify(ShowMessage);
        notify("Hello, Delegates!"); // Output: Hello, Delegates!
    }
}

```
7. **Multicast Delegates:**
	1. **Multicast delegates** are delegates that can hold references to more than one method. When invoked, a multicast delegate calls all the methods in its invocation list in the order they were added.
	2. A multicast delegate maintains a list of methods to be called.
	3. If the delegate returns a value, only the return value of the last method in the list is returned. For `void` return type methods, there is no return value.
	4. Methods are added to the delegate's invocation list using the `+` operator or the `Delegate.Combine` method.
	5. Methods can be removed using the `-` operator or the `Delegate.Remove` method.
	6. Example:
```
public class Program
{
    public delegate void Notify(string message);
    public static void ShowMessage(string message)
    {
        Console.WriteLine("Message: " + message);
    }
    public static void LogMessage(string message)
    {
        Console.WriteLine("Log: " + message);
    }
    public static void Main()
    {
        // Create a multicast delegate
        Notify notify = ShowMessage;
        notify += LogMessage;

        // Invoke the multicast delegate
        notify("Hello, Multicast Delegates!"); 

        // Output:
        // Message: Hello, Multicast Delegates!
        // Log: Hello, Multicast Delegates!
    }
}
```
