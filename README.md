#### DummyMicroservice
####To launch the application, either right-click the public static void main in PayRollApplication and select Run from your IDE, or: 
    
    Spring Initializr uses maven wrapper so type this:
    $ ./mvnw clean spring-boot:run

####Curl Commands
    When the app starts, we can immediately interrogate it…​
    curl -v localhost:8080/employees
    
    If you try and query a user that doesn’t exist…​
    curl -v localhost:8080/employees/99

    Creates a new Employee record, and then sends the content back to us…​
    curl -X POST localhost:8080/employees -H 'Content-type:application/json' -d '{"name": "Samwise Gamgee", "role": "gardener"}'

    Alter the user…​
    curl -X PUT localhost:8080/employees/3 -H 'Content-type:application/json' -d '{"name": "Samwise Gamgee", "role": "ring bearer"}'

    And you can delete…​
    curl -X DELETE localhost:8080/employees/3


