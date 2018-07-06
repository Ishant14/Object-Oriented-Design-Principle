# Object-Oriented-Design-Principle


SOLID principles are the set of principle fist given by Robert.C.Martin. SOLID principle as name given its set of principle that 
allows building SOLID software system (i.e. Application, Application Module), if one implement software according to this set of principle.

SOLID software system means its allows to build system that is

- Easy to maintain
- Easy to extend
- Easy to understand
- Easy to implement
- Easy to explain

SOLID principles are related with the design and maintenance of software system.Most of the developer mix SOLID principles with 
OOD principles and Design patterns. Below is the hierarchy of the principle from baisic to top level.

1. OOD Principle (Abstraction, Encapsulation, Inheritance, Polymorphism)
2. SOLID principle
3. Software Design Patterns (GOF patterns, Dependency injection & patterns)
4. Martin Flower’s Enterprise Application Architectures Pattern (additional but required)
5. Domain Driven Design Architecture (additional but required)

S.O.L.I.D is acronym for

**Single Responsibility Principle**

Principle is related to Designing software module, class or function that should perform only one task. 
So this principle is about Creation.

**Open/Close Principle**

Principle is applied after 1 (Single Responsibility Principle), again this principle is related to Designing module, class or function. 
But it about closing already designed thing for modification but opening designed thing for extension i.e. extending functionality. 
So this principle is about extension.

**Liskov Substitution Principle**

Principle is related to substitution of child in place of its parent. So principle is about relationship i.e. inheritance.

**Interface Segregation Principle**

Principle is related to designing of interfaces as one of the basic rules of designing says depends on abstraction. P
rinciple is about design interface such a way, so that client of interface not force to implement not required things. 
So principle is about efficient interface design.

**Dependency Inversion Principle**

Principle is related to designing decoupling modules, classes of software system. This principle mostly applied after 4 
(Interface Segregation principle) because interface are one form of abstraction and this principle is related to Details 
(module/class) should depend on abstraction, and abstraction should not depend on detail. So this principle is about creating 
loosely coupled system.


## Single Responsibility Principle

The Single Responsibility Principle is a SOLID principle defined by Robert C. Martin. In principle it says that an implementation 
(class / function) should perform only one task or implementation and it (class / function) should be changed for only one reason.

So in simple words it says that whatever the developer implements (class / function) in code during development should perform only 
one task and developer should only have one reason to change the implementation (class / function).

**Wrong interpretation of the Principle**

Most developers interpret to mean that a class should perform only one task. But it's not only classes, functions you implement in 
code during development should also perform only one task. So one should interpret it as meaning that an implementation should
perform only one task.

**Real Life Example of not following Single Responsibility Principle**

What happens when one can do more than one task? The following is an image of an example of it.One can perform multiple tasks, 
there is no question of that, but it's not going to provide quality / better output. So to get good quality/better output of work,
one should do one task at time.


**Example of not following Principle in Application Development**

In programming, in other words when developing code as in the following, the Order class is not following the principle.

```java
Public class OrderManager  
{  
    Public List < string > ValidateOrder()  
    {  
        //Code for validation    
    }  

    Public bool SaveOrder(OrderInfo order)   
    {  
        //Code for saving order    
    }  

    Public void NotifyCustomer()  
    {  
        //Code for notification     
　  }  
}
```

The preceding order class has the following three responsibility:

1. ValidateOrder: Validating an order placed by customer and return error message if any
2. SaveOrder: Saving an order placed by the customer and returns true/false
3. NotifyCustomer: Notifies the customer order is placed

**Method not following the principle.**

```java
public int SumOfAllCustomerOrder(int customerId)  
{  
    int sum = 0;  
    var query = "Select * from order where customerid = " + customerid;;  
    //query orders    
    foreach(Order in OrderCollection)   
    {  
        If(Order.Items.Count > 5)  
        Sum += Order.Price;  
    }  
    return sum;  
}
```

The preceding method has the following 2 responsibility:

1. fetch all the orders from the DB.
2. It went through all orders in the collection and does some of that


**Disadvantages of not following Single Responsibility Principle**

In programming if the developer creates a class/function that performs more than one task then that always causes problems in 
providing good quality. The following problems are related to a class performing more than one task:

- It's very difficult for the other developers (in other words developers unfamiliar with the class) to understand the class/function.
- It's difficult for the other developers to maintain the class/function or change the class/function.
- Writing test cases for the class/function also becomes difficult.


**How to determine if the Single Responsibility Principle has not been followed**

- Try to write a one line description of the class or method, if the description contains words like "And, Or, But or If" then that is a problem. An example of a description of a class as described above that does not follow the single responsibility principle is: “An Order class that performs order saving, notification to the customer and validates the order”.
- A class constructor takes more than three arguments or a method contains too many parameters.
- A class or method as an implementation that is is too long.
- A class that has low cohesion. Read more about cohesion : Cohesion

## Open Closed Principle

The Open Closed Principle is one of the SOLID principles defined by Robert C. Martin. The principle says “software entities 
(classes, modules, functions, etc.) should be open for extension, but closed for modification”.

So in simple words it says that an implementation (of a class or function), once created, should be closed for further modification, 
in other words one should not modify an implementation (of a class or function) of logic and/or functionality. 
One can do refactoring or resolve errors of implementation (of a class or function) but the implementation (of a class or function) 
is open for extension, in other words one can extend the implementation (of a class or function) of logic and/or functionality.

**Real Life Example of Open Closed Principle**

An electric adapter is a good example of this principle.

An adapter in the wall is always closed for modification, in other words we cannot change it once it is fitted or extended if 
we want more.But an adapter always provides a method of extension, so we can plug in an extension board of an adapter for more 
adaptation. So you plug in an extension board and extend an existing electric adapter fitted in wall.


**Example of not following the principle in Application Development**


In an organisation there are many kind of employee , suppose currently we have two type of employee ```PermanentEmployee``` and 
```TemporaryEmployee```. PermanentEmployee gets 10% anuall bonus whereas TemporaryEmployee gets 5% anual bonus. 

To calculate the anual bonus developer have developed the following class with methods to calculatebonus.

```java
public class Employee {

	private String name;
	private int id;
	private String employeeType;

	public float calculateBonus(int salary) {
		if (this.employeeType.equalsIgnoreCase("Permanent")) {
			return (float) (salary * 0.1);
		} else {
			return (float) (salary * 0.05);
		}
	}

	public String getEmployeeType() {
		return employeeType;
	}

	public void setEmployeeType(String employeeType) {
		this.employeeType = employeeType;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

}
```














