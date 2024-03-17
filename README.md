
```markdown
# Practical 01: Temperature Conversion Web Service

## Aim
The aim of this practical is to create a simple web service that converts temperature from Fahrenheit to Celsius and vice versa.

## Instructions

1. Create an ASP .NET Web Application.
2. Add a web service (ASMX).
3. Add the provided code to the web service:
```csharp
[WebMethod]
public double ctof(double c)
{
    return ((c * 1.8) + 32);
}

[WebMethod]
public double ftoc(double f)
{
    return ((f - 32) * 0.56);
}
```
4. Run the web service.
5. Invoke the methods and test if they are working correctly.
6. Add a new Web Form.
7. Add two Textboxes and one Radio Button list.
8. For the Radio Button list, set the properties as follows:
   - Collections → Add "Celsius" and "Fahrenheit"
   - Set AutoPostBack to True.
9. Double-click on the Radio Button list and write the following code:
```csharp
mywebservice ws = new mywebservice();
switch (RadioButtonList1.SelectedIndex)
{
    case 0:
        TextBox2.Text = ws.ftoc(Convert.ToDouble(TextBox1.Text)).ToString();
        break;
    case 1:
        TextBox2.Text = ws.ctof(Convert.ToDouble(TextBox1.Text)).ToString();
        break;
}
```
10. Add a service reference: Advanced → Add Web Reference, and select the current web service.
11. Run the web form.














```

#Practical 02

```markdown
### Aim: Implementing Request-Response and One-Way Operations in a WCF Service

The aim of this program is to create a WCF service application that can receive requests and return responses in two ways: Request-Response and One-Way operations.

## Instructions

1. Create a new WCF service application.

2. Open `Service1.svc.cs` and make the following changes to implement various operations:

```csharp
public void Subtract(double n1, double n2)
{
    double result = n1 - n2;
    System.Diagnostics.Debug.WriteLine("subtract({0},{1}) ={2}", n1, n2, result);
}

public void Multiply(double n1, double n2)
{
    double result = n1 * n2;
    System.Diagnostics.Debug.WriteLine("Multiply({0},{1}) ={2}", n1, n2, result);
}

public void Divide(double n1, double n2)
{
    double result = n1 / n2;
    System.Diagnostics.Debug.WriteLine("Divide({0},{1}) ={2}", n1, n2, result);
}

public string SayHello(string name)
{
    System.Diagnostics.Debug.WriteLine("SayHello({0})", name);
    return "hello " + name;
}

public double Add(double n1, double n2)
{
    double result = n1 + n2;
    return result;
}
```

3. Open `IService1.cs` and make the following changes to the code:

```csharp
[OperationContract(IsOneWay = true)]
void Subtract(double n1, double n2);

[OperationContract(IsOneWay = true)]
void Multiply(double n1, double n2);

[OperationContract(IsOneWay = true)]
void Divide(double n1, double n2);

[OperationContract]
string SayHello(string name);

[OperationContract]
double Add(double n1, double n2);
```

4. Click on `Service1.cs` and run the service.

5. Test all the services:
   - Subtraction, Multiplication, and Division should be one-way operations.
   - Saying hello and Addition should be request-response operations.


```


















````
##Practical 03

```markdown
### Aim: Develop Client to Consume Web Services from Different Platforms

The aim of this task is to create a client application that consumes a web service developed in a different platform.

## Instructions

1. Create a new [ASP.NET](http://ASP.NET) Web Application project.

2. Add a web service to the project.

3. Make changes to the web service code to customize its response, for example:

```csharp
return "This web service is created in ASP.NET Web Service Web Application";
```

4. Run the web service to ensure it's functioning correctly.

5. Click on the service description to access the WSDL file and copy the URL.

6. Keep the web service running in Visual Studio.

7. Open NetBeans and create a Java Web Application project.

8. Add a web service client to the Java project and paste the copied WSDL URL.

9. Add a JSP page to the Java project.

10. Go to the Web Service Client Resources and call the web service application.

11. Select the operation you want to invoke, such as "Hello World".

12. Run the JSP file to test the functionality of the web service client.








#Practical 05

```markdown
### Aim: Develop a JAX-WS web service to perform arithmetic operations and create a servlet/JSP to consume the web service.

The aim of this task is to create a JAX-WS web service to perform arithmetic operations and then develop a servlet or JSP to consume this web service.

## Instructions

1. Open NetBeans IDE.

2. Create a new web application project.

3. Add a web service to the project:
   - Right-click on the project.
   - Choose "New" -> "Web Service".
   - Define the operations you want to include in the web service, e.g., addition, subtraction, etc.

4. Test the web service to ensure it's functioning correctly.

5. Create another web application project in NetBeans.

6. Add a web service client to this project:
   - Right-click on the project.
   - Choose "New" -> "Web Service Client".
   - Select the previously created web service project.

7. Add a servlet to the new web application project:
   - Right-click on the project.
   - Choose "New" -> "Servlet".

8. Drag and drop the methods of the web service (e.g., addition) to the servlet in the NetBeans visual editor.

9. Write code in the servlet to handle the form submission and invoke the web service method. For example:

```java
out.println("<form>");
out.println("Enter First number: <input type='text' name='n1'/>");
out.println("Enter second number: <input type='text' name='n2'/>");
out.println("<input type='submit' value='add'/></form>");
out.println("<h1>Addition of two numbers</h1>" + add(Integer.parseInt(request.getParameter("n1")), Integer.parseInt(request.getParameter("n2"))));
```

10. Run the application to test the servlet and the consumption of the web service.























### Practical 07: Define a RESTful Web Service for CRUD Operations

**Aim:** Develop a RESTful web service to handle CRUD operations for storing details in a database.

**Procedure:**

1. **Project Setup:**
   - Create a new web application in Java NetBeans named "restful_service".

2. **Create Entity Class:**
   - Define an entity class for storing details in the database.

3. **Add Student Name Property:**
   - Within the entity class, after setting the ID property, add a property for student name (`sname`).

```java
private String sname;
```

4. **Generate Highlighted Text:**
   - Generate the highlighted text in the image to set up the necessary components.

5. **Add JSF Pages:**
   - Generate JSF (JavaServer Faces) pages from the entity class to create a user interface for managing student details.

6. **Add RESTful Web Services:**
   - Generate RESTful web services from the entity class to handle CRUD operations (Create, Read, Update, Delete).

7. **Deployment and Testing:**
   - Deploy and run the project, ensuring that Oracle is not running on port 8080 to avoid conflicts.







### Practical 09: AJAX Web Service Implementation

**Aim:** Implement an AJAX web service for performing addition.

**Procedure:**

1. **Create [ASP.NET](http://ASP.NET) Web Application:**
   - Start by creating a new [ASP.NET](http://ASP.NET) web application project.

2. **Add AJAX Web Service:**
   - Within the project, add a web service specifically for AJAX.

3. **Add Addition Method to Web Service:**
   - Insert the following code into the web service to define an addition method:
   
```csharp
public int addition(int a, int b)
{
   return a + b;
}
```

4. **Create Web Form:**
   - Add a web form to the project where users can input numbers and see the result of addition.

5. **Add Input Fields and Result Placeholder:**
   - Within the web form, include two text boxes with IDs `n1` and `n2` for entering numbers.
   - Add a `<div>` element with an ID `ans` to display the result of addition.

6. **Add ScriptManager:**
   - Insert a ScriptManager component in the markup of the web form to handle AJAX requests:

```csharp
<asp:ScriptManager ID="ScriptManager1" runat="server">
 <Services>
 <asp:ServiceReference Path="~/Service1.svc" />
 </Services>
</asp:ScriptManager>
```

7. **Complete the HTML Markup:**
   - Add the remaining HTML markup for the form.

8. **Implement JavaScript Function for Addition:**
   - Write a JavaScript function called `add()` to call the addition method from the web service.
   - Define an `onSuccess()` function to handle the result of the addition.

9. **Run the Web Form:**
   - Launch the web form to test the AJAX web service for addition functionality.



### Practical 10: Using the Binding Attribute in WCF

**Aim:** Demonstrate the use of the binding attribute of an endpoint element in WCF.

**Procedure:**

1. **Create a New WCF Service Application:**
   - Begin by creating a new WCF Service Application in [ASP.NET](http://asp.net/).

2. **Define Operation Contract:**
   - In the IService.cs interface, add the following code to define an operation contract for addition:
   
```csharp
[OperationContract]
int add(int a, int b);
```

3. **Implement Addition Method:**
   - Add the implementation of the `add()` method in the Service1.svc.cs class:
   
```csharp
public int add(int a, int b)
{
    return a + b;
}
```

4. **Run the Project:**
   - Start the project to deploy the service and access it.

5. **Access Service Endpoint:**
   - Open the service.svc in a web browser and copy the address from the browser.

6. **Create Web Application in NetBeans:**
   - Switch to NetBeans and create a new web application project.

7. **Add Web Client Service:**
   - Add a web client service to consume the WCF service.

8. **Create JSP Page:**
   - Within the project, create a new JSP page.

9. **Drag and Drop Web Service Reference:**
   - Drag and drop the `add()` function from the web service reference onto the JSP page.

10. **Modify JSP Code:**
    - Edit the JSP page to include input fields for numbers, a submit button, and code to call the `add()` function.

```
<form name="myform">
 Enter number 1: <input type="text" name="n1" id="n1"><br/>
 Enter number 2: <input type="text" name="n2" id="n2"><br/>
 <input type="submit" value="add">
 <br>
 <% if(request.getParameter("n1")!=null &&
request.getParameter("n2")!=null)
 {
 int x=Integer.parseInt(request.getParameter("n1"));
 int y=Integer.parseInt(request.getParameter("n2"));
 try {
 org.tempuri.Service1 service = new org.tempuri.Service1();
 org.tempuri.IService1 port =
service.getBasicHttpBindingIService1();
 // TODO process result here
 java.lang.Integer result = port.add(x, y);
 out.println("Addition of two number is : "+result);
 }
 catch (Exception ex)
 {
// TODO handle custom exceptions here
 }
 }
 %>
```

11. **Run the JSP Page:**
    - Execute the JSP page to test the interaction with the WCF service. Ensure that the [ASP.NET](http://ASP.NET) page hosting the service is still running.

12. **Conclusion:**
    - You have successfully demonstrated the use of the binding attribute of an endpoint element in WCF by consuming the service in a Java web application.










