# REST API means Representational State Transfer Application Programming Interface.
In simple words, a REST API is a way for two applications to communicate with each other over the internet using HTTP.
Why REST API is used
To connect frontend (React, Angular, Mobile app) with backend (Java, Spring Boot, ASP.NET, Node.js)
To send and receive data (mostly in JSON format)
To make applications scalable, fast, and independent

What is ASP.NET MVC Core?
ASP.NET MVC Core is a web framework by Microsoft used to build:
Web applications
Websites
REST APIs

It follows the MVC design pattern:
M – Model → Data & business logic
V – View → UI (HTML pages)
C – Controller → Handles request & response

| Folder      | Purpose          |
| ----------- | ---------------- |
| Controllers | Handles requests |
| Models      | Data classes     |
| Views       | UI pages         |
| wwwroot     | CSS, JS, images  |
| Program.cs  | App start point  |

2️⃣ MVC Components (Simple Meaning)

🔹 Model
Represents data
Contains business logic
Communicates with database
📌 Example: Student, Employee

🔹 View
Represents UI
Contains HTML + Razor
Displays data to user
📌 Example: Index.cshtml

🔹 Controller
Acts as middleman
Receives request
Calls Model
returns View
📌 Example: HomeController

Browser
   ↓  (URL Request)
Routing Engine
   ↓
Controller
   ↓
Action Method
   ↓
Model (optional)
   ↓
View
   ↓
Browser (HTML Response)

Role of Routing (Important)
Routing maps:
URL → Controller → Action
Default route in Program.cs:
pattern: "{controller=Home}/{action=Index}/{id?}"
Meaning:
Controller default = Home
Action default = Index
id = optional

8️⃣ Questions (Quick)
Q1. What is MVC?
✔ Design pattern separating Model, View, Controller
Q2. Who handles request in MVC?
✔ Controller
Q3. Where is UI written?
✔ View
Q4. What connects URL to Controller?
✔ Routing Engine

| File/Folder      | Purpose         |
| ---------------- | --------------- |
| Controllers      | Handle requests |
| Models           | Data & logic    |
| Views            | UI              |
| wwwroot          | Static files(css,js,
                     image,bootstrap)|
| Program.cs       | App startup     |
| appsettings.json | Config          |

6️⃣ IActionResult (Important)
Action methods return:
IActionResult
Common return types:
View()
Content()
Json()
RedirectToAction()
NotFound()

A web application is a software program that runs on a web server and is accessed through a web browser using the internet. 
You don’t need to install it on your computer—just open a browser and use it.
ASP stands for Active Server Pages.
It is a server-side web technology by Microsoft used to create dynamic web applications.
Today, ASP is mainly used as ASP.NET and ASP.NET Core.

ASP - uses VB script language
ASP.net - use language C#
php - use language php script
jsp and servlet - use language java


for ASP.net
- html
- css-
- js 
- ASP.net with c#
- web server(IIS - Internet Information Services) 


<hr>

## 1️⃣ Data Management with ADO.NET – Overview

```
ADO.NET is a data access technology used in .NET applications to interact with databases such as SQL Server, Oracle, MySQL, etc.
Key Features
Works in connected and disconnected modes
High performance
Supports asynchronous operations
Uses XML-based DataSet
Provider-based architecture
```

## 🔷 ADO.NET Data Access Models

ADO.NET supports two ways to work with data: <br>
1️⃣ Connected Architecture <br>
2️⃣ Disconnected Architecture <br>

1️⃣ Connected ADO.NET Architecture

```
🔹 What is Connected Architecture?
The database connection remains OPEN
Data is read directly from database
Uses SqlDataReader
Very fast and memory efficient

🔹 Components Used
SqlConnection
SqlCommand
SqlDataReader

🔹 Flow (Exam-Friendly)
Open Connection
   ↓
Execute Command
   ↓
Read Data using DataReader
   ↓
Close Reader
   ↓
Close Connection

🔹 Connected Architecture Example

using Microsoft.Data.SqlClient;

SqlConnection con = new SqlConnection(
 "Data Source=.;Initial Catalog=TestDB;Integrated Security=True");

SqlCommand cmd = new SqlCommand(
 "SELECT * FROM Employees", con);

con.Open();   // connection stays open

SqlDataReader dr = cmd.ExecuteReader();

while (dr.Read())
{
    Console.WriteLine(dr["Name"]);
}

dr.Close();
con.Close();

🔹 Characteristics
| Feature     | Connected      |
| ----------- | -------------- |
| Connection  | Always open    |
| Speed       | Very fast      |
| Memory      | Low            |
| Data Access | Read-only      |
| Data Update | Not allowed    |
| Best For    | Real-time data |
```

2️⃣ Disconnected ADO.NET Architecture
```
🔹 What is Disconnected Architecture?
Connection opens only while fetching data
Data stored in memory (DataSet/DataTable)
Connection is closed immediately
Uses SqlDataAdapter

🔹 Components Used
SqlConnection
SqlCommand
SqlDataAdapter
DataSet
DataTable

🔹 Flow (Exam-Friendly)
Open Connection
   ↓
Fetch Data using DataAdapter
   ↓
Store in DataSet/DataTable
   ↓
Close Connection
   ↓
Work on Data Offline

🔹 Disconnected Architecture Example
using Microsoft.Data.SqlClient;
using System.Data;

SqlConnection con = new SqlConnection(
 "Data Source=.;Initial Catalog=TestDB;Integrated Security=True");

SqlDataAdapter da = new SqlDataAdapter(
 "SELECT * FROM Employees", con);

DataSet ds = new DataSet();

da.Fill(ds, "Employees");  // connection auto open & close

DataTable dt = ds.Tables["Employees"];

foreach (DataRow row in dt.Rows)
{
    Console.WriteLine(row["Name"]);
}

| Feature     | Disconnected           |
| ----------- | ---------------------- |
| Connection  | Closed after fetch     |
| Speed       | Slower than DataReader |
| Memory      | Higher                 |
| Data Access | Read & Write           |
| Data Update | Allowed                |
| Best For    | Web apps, offline work |
```

| Feature        | Connected     | Disconnected |
| -------------- | ------------- | ------------ |
| Main Object    | SqlDataReader | DataSet      |
| Connection     | Always open   | Closed early |
| Mode           | Online        | Offline      |
| Performance    | High          | Medium       |
| Update Support |  No           |  Yes         |
| Network Load   | High          | Low          |
| Use Case       | Live data     | Web apps     |
















