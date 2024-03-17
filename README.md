```
Practical 01

Aim: Write a program to implement to create a simple web service that converts the temperature from Fahrenheit to Celsius and vice versa

Create a new ASP.NET project


Add web service 


Add a web form 






WebService code:

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Services;

namespace TemperatureConvert
{
    /// <summary>
    /// Summary description for WebService1
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [System.ComponentModel.ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line. 
    // [System.Web.Script.Services.ScriptService]
    public class WebService1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
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
    }
}


Mypage.aspx Code:
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace TemperatureConvert
{
    public partial class mypage : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }

        protected void RadioButtonList1_SelectedIndexChanged(object sender, EventArgs e)
        {
            WebService1 ws = new WebService1();
            switch (RadioButtonList1.SelectedIndex)
            {
                case 0: TextBox2.Text = ws.ftoc(Convert.ToDouble(TextBox1.Text)).ToString(); break;
                case 1: TextBox2.Text = ws.ctof(Convert.ToDouble(TextBox1.Text)).ToString(); break;
            }
        }
    }
}




Practical 02

Aim: Write a program to implement the operation can receive request and will return a response in two ways A)One-Way operation and B)Request-Response

Create a WCF Service Application in Visual Studio


Click on the IService1.cvs file and add the code 


using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Web;
using System.Text;

namespace Practical_02
{
	// NOTE: You can use the "Rename" command on the "Refactor" menu to change the interface name "IService1" in both code and config file together.
	[ServiceContract(Namespace ="https://Microsoft.ServiceModel.Samples")]
	public interface IService1
	{
    	[OperationContract(IsOneWay =true)]
    	void Subtract(double n1, double n2);

    	[OperationContract(IsOneWay =true)]
    	void Multiply(double n1, double n2);

    	[OperationContract(IsOneWay =true)]
    	void Divide(double n1, double n2);

    	[OperationContract]
    	string Hello(string name);
    	[OperationContract]
    	double Add (double n1, double n2);
	}
   
	}





Now Click on IService.cs and add the following code 


using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Web;
using System.Text;

namespace Practical_02
{
	// NOTE: You can use the "Rename" command on the "Refactor" menu to change the class name "Service1" in code, svc and config file together.
	// NOTE: In order to launch WCF Test Client for testing this service, please select Service1.svc or Service1.svc.cs at the Solution Explorer and start debugging.
	public class Service1 : IService1
	{

    	public void Subtract(double n1, double n2)
    	{
        	double result = n1 - n2;
        	System.Diagnostics.Debug.WriteLine("Subtract({0}, {1}) = {2}", n1, n2, result);
    	}

    	public void Multiply(double n1, double n2)
    	{
        	double result = n1 * n2;
        	System.Diagnostics.Debug.WriteLine("Multiply({0}, {1}) = {2}", n1, n2, result);
    	}

    	public void Divide(double n1, double n2)
    	{
        	double result = n1 / n2;
        	System.Diagnostics.Debug.WriteLine("Divide({0}, {1}) = {2}", n1, n2, result);
    	}

    	public string Hello(string name)
    	{
     	 
        	System.Diagnostics.Debug.WriteLine("Say Hello({0})", name);
        	return "hello" + name;
    	}

    	public double Add(double n1, double n2)
    	{
        	double result = n1 + n2;
        	return result;
    	}


	}
}



Click on Service.svc and run the project



Following dialog box will be shown 




Click on Subtract and check for One-Way Operation






Click on Add and check for Request Response 


















Practical 03

Aim: Write a program to implement business UDDI Registry entry extraction

Download JUDDI from the official Link: https://archive.apache.org/dist/juddi/juddi/3.3.9/juddi-distro-3.3.9.zip

 Extract the file


Install JDK 8


Make sure JDK 8 is installed and all paths are set as below:

 To set the path open edit environment Variable 



Click on Environment Variable


Set the CATALINA_HOME path till the home folder of tomcat in JUDDI-Distro folder

C:\Downloads\juddi-distro-3.3.9\juddi-distro-3.3.9\juddi-tomcat-3.3.9

Set the CLASSPATH path as shown

C:\Downloads\juddi-distro-3.3.9\juddi-distro-3.3.9\juddi-tomcat3.3.9\lib\servlet-api.jar

Set your PATH for java

a. C:\Program Files\Java\ jdk1.8.0_311\bin
b. %CATALINA_HOME%
Set your JAVA_HOME path

C:\Program Files\Java\jdk1.8.0_311

Go to the following path
 (C:\Users\suraj\Downloads\juddi-distro-3.3.9\juddi-distro3.3.9\juddi-tomcat-3.3.9\bin)

In the bin folder (juddi-tomcat-3.3.9\bin) double click on makebase.bat file (it’s the windows batch file to make database for JUDDI).

Go into                                                                                                                                     

C:\Users\suraj\Downloads\juddi-distro-3.3.9\juddi-distro-3.3.9\juddi-tomcat3.3.9\conf\

Open the Catalina property file named as catalina.property and add the following line:
javax.xml.accessExternalDTD=all

In the end of the file and save it and close the file. 

In the bin folder (juddi-tomcat-3.3.9\bin) double click on startup.bat file (it’s the windows batch file to start the server). In case there is a start-up error check if port no:8080 is free. Some cases oracle server is switched on. Go in services and stop all oracle services.

Now type localhost:8080 in the web browser:


 



Open netbeans and create a new project .select Java application and create the project


Type the following code

/*
* To change this license header, choose License Headers in Project Properties.
* To change this template file, choose Tools | Templates
* and open the template in the editor.
*/
package uddi;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;
import java.util.Base64;
public class Uddi {
 /**
 * @param args the command line arguments
 */
 public static void main(String[] args) {
 try {
 // Set UDDI registry information
 String inquiryURL = "http://localhost:8080/juddiv3/services/inquiryv2?wsdl";
 // Set authentication information if required
 String username = "uddiadmin";
 String password = "da_password1";
 // Create SOAP request payload
 String soapRequest = "<soapenv:Envelope
xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" " +
 "xmlns:urn=\"urn:uddi-org:api_v2\">\n" +
 " <soapenv:Header/>\n" +
 " <soapenv:Body>\n" +
 " <urn:find_business generic=\"2.0\" maxRows=\"10\">\n" +
 " <urn:name>*</urn:name>\n" +
 " </urn:find_business>\n" +
 " </soapenv:Body>\n" +
 "</soapenv:Envelope>";
 // Set up HTTP connection
 URL url = new URL(inquiryURL);
 HttpURLConnection connection = (HttpURLConnection) url.openConnection();
 connection.setRequestMethod("POST");
 connection.setRequestProperty("Content-Type", "text/xml;charset=UTF-8");
 connection.setDoOutput(true);
 // Set up HTTP basic authentication
 if (username != null && password != null) {
 String credentials = username + ":" + password;
 String encodedCredentials =
java.util.Base64.getEncoder().encodeToString(credentials.getBytes(java.nio.charset.StandardCharsets
.UTF_8));
 connection.setRequestProperty("Authorization", "Basic " + encodedCredentials);
 }
 // Send SOAP request
 try (OutputStream os = connection.getOutputStream()) {
 byte[] input = soapRequest.getBytes(java.nio.charset.StandardCharsets.UTF_8);
 os.write(input, 0, input.length);
 }
 // Get SOAP response
 int responseCode = connection.getResponseCode();
 System.out.println("HTTP Response Code: " + responseCode);
 // Read response
 try (BufferedReader br = new BufferedReader(new
InputStreamReader(connection.getInputStream()))) {
 String line;
 StringBuilder response = new StringBuilder();
 while ((line = br.readLine()) != null) {
 response.append(line).append("\n");
 }
 // TODO: Parse the XML response and extract business names and service names
 System.out.println("Response from JUDDI registry: " + response.toString());
 }
 // Close the connection
 connection.disconnect();
 } catch (IOException e) {
 e.printStackTrace();
 }
 }

}

Observe the output

Practical 04

Aim: Develop a Client that consumes web services developed on different platforms.

Create a new ASP.NET Web Application






Add a webservice


Add the following code

    public class WebService1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "You are executing web service in ASP.NET";
        }
    }
}




Run the web service 


Click on Service Description and copy the link 


Open NetBeans and create a new Web Application 




Add a new Web Service Client 



Web Service Client Resources → call web service application


Save and run the file 


Conclusion: we have successfully create an application in visual studio which is consumed by java net beans using Glassfish server (Develop Client which consumes web services developed in different platform)















Practical 05
Aim: Write a JAX-WS web service to perform the following operations. Define a Servlet / JSP that consumes the web service.

Create a new Java Web Application in NetBeans 8.1


Create a new WebService 








Add operation 






Run the file 




 Create another web application


Now ad a Web service Cilent and Connect it to the webservice


Add a servlet file to your consume app 


Drag and drop the addition method()



Add the following code to the servlet processRequest function


out.println("<form>");
 out.println("Enter First number: <input type='text' name='n1'/>");
 out.println("Enter second number: <input type='text' name='n2'/>");
 out.println("<input type='submit' value='add'/></form>");
 out.println("<h1>Addition of two
number</h1>"+add(Integer.parseInt(request.getParameter("n1")),Integer.parseInt(request.get
Parameter("n2")))+"</h1>");
Run the application 





















Practical 06
Aim: Define a web service method that returns the contents of a database in a JSON string. The contents should be displayed in a List Format. 

Create a new ASP.Net Web Application 




Make sure you have installed Data storage and processing, SQL Express for Visual Studio 2022


Go to Server Explorer and create a new SQL database 




Add a new Web Service 


Add the following code:

  [WebMethod]
  public void GetAllStudents()
  {
      List<student> slist = new List<student>();
      string cs =
      ConfigurationManager.ConnectionStrings["ApplicationServices"].ConnectionString;
      using (SqlConnection con = new SqlConnection(cs))
      {
          SqlCommand cmd = con.CreateCommand();
          cmd.Connection = con;
          cmd.CommandType = System.Data.CommandType.Text;
          cmd.CommandText = "select * from student";
          con.Open();
          SqlDataReader rdr = cmd.ExecuteReader();
          while (rdr.Read())
          {
              student s = new student();
              s.name = rdr["name"].ToString();
              s.rollno = Convert.ToInt32(rdr["roll no"]);
              s.emailid = rdr["email"].ToString();
              slist.Add(s);
          }
      }
      JavaScriptSerializer js = new JavaScriptSerializer();
      Context.Response.Write(js.Serialize(slist));




Create a class called ‘Student’


Add the following code:

public class student
{
public string name { get; set; }
public int rollno { get; set; }
public string emailid { get; set; }
}



Create a new Table 

CREATE TABLE [dbo].[Table_Student] (
    [StudentId] INT IDENTITY(1,1) PRIMARY KEY,
    [Name] VARCHAR(100) NOT NULL,
    [RollNo] BIGINT NULL,
    [Email] VARCHAR(100) NULL
);




Insert new Query 

INSERT INTO [dbo].[Table_Student] ([Name], [RollNo], [Email])
VALUES ('John Doe', 123456, 'john.doe@example.com');

INSERT INTO [dbo].[Table_Student] ([Name], [RollNo], [Email])
VALUES ('John2 Doe', 1234567, 'john2.doe@example.com');





Go to Web.config file and make changes 

<connectionStrings>
	<add name="ApplicationServices" connectionString="Data Source=TANISH\SQLEXPRESS;Initial Catalog=student;Integrated Security=True;Pooling=False;Encrypt=True;Trust Server Certificate=True"
	providerName="System.Data.SqlClient"/>
</connectionStrings>


Run webservice and click on ‘GetAllStudents’

















































Practical 07
Aim:  Define a RESTful web service that accepts the details to be stored in a database and performs CRUD operation.

Create a new web application


Create a new Entity Class ‘Student’




Insert code after SET ID Property 


Add property student name 



Add JSF pages from entity class






Now add RestFull webservices from entity class as shown below in image



































Practical 08
Aim: Implement a typical service and a typical client using WCF

Create a new web application




Create a new SQL database and create a table with dummy values 

CREATE TABLE [dbo].[student]
(
	[Id] INT NOT NULL PRIMARY KEY, 
    [name] NCHAR(10) NULL, 
    [address] NCHAR(10) NULL
)

INSERT INTO [dbo].[student] ([Id], [name], [address])
VALUES (1, 'John Doe', '123 Main Street'),
       (2, 'Jane Smith', '456 Elm Street'),
       (3, 'Alice Johnson', '789 Oak Avenue');





Add a WCF Service 


Add the following code 

    public interface IService1
    {
        [OperationContract]
        student GetStudent();
    }
    [DataContract]
    public class student
    {
        public student()
        {
            this.studentsTable = new DataTable("student");
        }
        [DataMember]
        public DataTable studentsTable { get; set; }
    }
}



Add the connection string in Web.config file 

<configuration>
	<connectionStrings>
		<add name="APP" connectionString="Data Source=TANISH\SQLEXPRESS;Initial Catalog=student8;Integrated Security=True;Pooling=False;Encrypt=True;Trust Server Certificate=True"/>
	</connectionStrings>



Add the following code in Service1.svc.cs file 

    public class Service1 : IService1
    {
        public student GetStudent()
        {
            string constr = ConfigurationManager.ConnectionStrings["APP"].ConnectionString;
            using (SqlConnection con = new SqlConnection(constr))
            {
                using (SqlCommand cmd = new SqlCommand("select * from student8"))
                {
                    using (SqlDataAdapter sda = new SqlDataAdapter())
                    {
                        cmd.Connection = con;
                        sda.SelectCommand = cmd;
                        using (DataTable dt = new DataTable())
                        {
                            student s = new student();
                            sda.Fill(s.studentsTable);
                            return s;
                        }

                    }
                }
            }
        }
    }
}



Run this service in browser 


Add a WCF Web Reference 




Add a WebForm 


Add a GridView 


Write the following code in page load 

 ServiceReference1.Service1Client sc = new ServiceReference1.Service1Client();
 GridView1.DataSource = sc.GetStudent().studentsTable;
 GridView1.DataBind();

































Practical 09
Aim: Use WCF to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX)Service.

Create a new ASP.NET Web Application

Name you project (“AJAX-Enabled-WCF”). Make sure to change the .NET Framework to 4.8
Create an empty project and uncheck configure for HTTP
Create an empty project and uncheck configure for HTTP
Add a new Web form.
Design the webpage to have two textboxes and one button. Make sure to use HTML
Components
 Add a WCF Service(Ajax-enabled)
 Add the following code as shown below in the image

[OperationContract]
public int addition(int a, int b)
{
return a + b;
}

 Add an AJAX Extension called ScriptManager as shown below
Go in the markup section and add the code in between the ScriptManager tag as shown Below:

<asp:ScriptManager ID="ScriptManager1" runat="server">
<Services>
<asp:ServiceReference Path="~/Service1.svc" />
</Services>
</asp:ScriptManager><br />

The below given code is entire markup code with java script

<body>
<form id="form1" runat="server">
<div>
Enter the First Number:<input id="n1" type="text" /><br />
Enter the Second Number:<input id="n2" type="text" /><br />
<input type="button" value="Add" onclick="add()"/><br />
<span id="ans"></span>
<asp:ScriptManager ID="ScriptManager1" runat="server">
<Services>
<asp:ServiceReference Path="~/Service1.svc" />
</Services>
</asp:ScriptManager><br />
</div>
<div>&nbsp;</div>
</form>
</body>
</html>
<script type="text/javascript">
function add() {
var a, b;
a = parseInt(document.getElementById("n1").value);
b = parseInt(document.getElementById("n2").value);
Service1.addition(a, b, onSuccess);
}
function onSuccess(result) {
var myres = $get("ans");
myres.innerHTML = "addition of two numbers is " + result;
}
</script>

The highlighted code in yellow is the service name created above. Make sure you
replace with the name you have given. Here its default name.
Run the web form and you should get the output running.



























Practical 10
Aim: Demonstrates using the binding attribute of an endpoint element in WCF

1. Create a new WCF Service Application in ASP.NET


2. Add the following code in the interface (IService.cs) as shown below:

OperationContract]
int add(int a,int b);

3. Add the following code in the class (“service1.svc.cs”)

public int add(int a,int b)
{
return a + b;
}

4. Now run the project: you will see the screen below


5. Don’t stop the project or close this screen. Minimise this screen and open the service.svc in the browser as shown below: copy the address and paste it in the Browser:


6. Now click the first link and copy the link from the browser:



7. Now open netbeans to consume this service:
Create a new web application:


8. Now add web client service as shown below:


9. Paste the link here as shown below:


10. Click finish to create. Then create a jsp page.


11. Drag and drop the add function from the web service reference as shown below

12. Make Changes to the code:

 <%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
    	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    	<title>JSP Page</title>
	</head>
	<body>
    	<form name="myform">
        	Enter number 1: <input type="text" name="n1" id="n1"><br/>
        	Enter number 2: <input type="text" name="n2" id="n2"><br/>
        	<input type="submit" value="add">
    	</form>
    	<%
    	if(request.getParameter("n1")!=null && request.getParameter("n2")!=null)
    	{
        	int x=Integer.parseInt(request.getParameter("n1"));
        	int y=Integer.parseInt(request.getParameter("n2"));
        	out.println("<br>");
        	// start web service invocation
        	out.println("<hr/>");
        	try {
            	org.tempuri.Service1 service = new org.tempuri.Service1();
            	org.tempuri.IService1 port = service.getBasicHttpBindingIService1();
            	// TODO initialize WS operation arguments here
            	java.lang.Integer a = Integer.valueOf(x);
            	java.lang.Integer b = Integer.valueOf(y);
            	// TODO process result here
            	java.lang.Integer result = port.add(a, b);
            	out.println("Addition of two number is : "+result);
        	} catch (Exception ex) {
            	// TODO handle custom exceptions here
        	}
        	out.println("<hr/>");
        	// end web service invocation
    	}
    	%>
	</body>
</html>





13. Now run the JSP page. Make sure you asp.net Page in still running.

```
