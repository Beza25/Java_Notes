# Java_Notes
----------------------------------------------Home Controller---------------------------------------------------------------------
@ReqestParam: 
 @RequestMapping("/StudentConfirmed")
    public String loadForm(@RequestParam("login") String login, Model model){
        model.addAttribute("loginval", login);
        return "studentConfirmed";
    }

***Validation
 @RequestMapping("/StudentConfirmed")
    public String loadForm(@Valid Student student BindingResult result){
        if(result.hasErrors()){
		return "/studentForm";
		}
		return "studentConfirmed;
    }


- @ReqestParam: expects a parameter (either in the URL as a GET request or POST request) that is called login
				: and passes the value to the model as a "loginval"
				: The html can now acess the login string as "loginval"
				
-----------------------------------------------------HTML---------------------------------------------------------------
				
- th:action: is an attribute that specifice what happens after the submit button is clicked
		   : tells the SpringBoot what endpoint to use to process the form data
- th:inline: indacates the value of text to be displayed is shown within the tag
		   : Need to use [[]] to make sure the thymeleaf expresstion is evalueated 
- th:fileds: fields of an object of a class refered in html
- th:object: indcates the answers the user gives is stored in an object 
     <form action: "#" th:action="@{/songform}" th:object="${song}" method = "post">...</form>
	 
	 th:action --> specifice the end point  || th:object --> says store the info in objec called song || method = post --> it happens after the sumbit button is clicked
***Validation
-th:if ="${fields.hasErrors('id')}" --> gets the return value from Binding result  
				id --> a field in java bean
- th:errors = "*{id}" --> builds the default error message for the field if there are errors. 

-----------------------------------------------Thymeleaf Expressions---------------------------------------------------------------
- *{} : referes to predifined object
- ${} : a variable is expected and the value should be displayed
- #{} : referes to predufined message should be displayed 
- @{} : referes to 
- [[...]] : making sure your thymeleaf expression is valuated

------------------------------------------------Java Bean------------------------------------------------------------------------------
Validation 
- @Not nul
- @Min(3)
- @Size(min = 8 max = 25)
-----------------------------------------------Database Annotation in Java Bean---------------------------------------------------
- @Entit --> creates table in your database
				location of table is determined by the the application properties in this case it is H2-database (in memory)
				the fields in the java bean determines the type of the data with its constraints
- @Id --> indicates that the field is a unique identifier that will be used for each row in the database\
- @GenratedValue --> identifier will be generated  && (Strategy = GenerationType.AUTO)--> unique number will automatically assigned to each row
-----------------------------------------------Data Base------------------------------------------------------------------------------
- H2-database : Creating Spring Boot application that uses in-memory database called H2 that stores dat
***Appilicatin properties 
- spring.h2.console.enabled=true  --> permits acess to the databae outside the appliction (using the h2 console)
- spring.h2.console.path=/h2-console --> allows the you to browse the data base  to  vies the data localhost:8080/h2-console
- spring.jpa.hibernate.ddl-auto=create --> allows the application to create database tables. [Everytime you run your application it creates tabelbes to store the dayat ]
- spring.datasource.url = ... --> this specifiecs the url of the connected database 
