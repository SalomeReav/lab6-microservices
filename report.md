# PRIMARY GOAL SOLUTION

### First Part

- First we run the registration service with the command: 
`./gradlew :registration::bootRun`
Then in `localhost:1111` we can check server eureka is running. 


- Now we run an account in port 2222 with the command: `./gradlew :accounts:bootRun`
Then we can see this on terminal: 
![image](https://user-images.githubusercontent.com/59259958/147988439-d90a41ba-fb32-4ac7-b86c-f4b743e5831b.png)

And in `localhost:2222` we can see the following: 

![image](https://user-images.githubusercontent.com/59259958/147988639-6bd29a07-d508-46bc-83a4-1b1fccc765f5.png)

- Now we run a web service with the command: `./gradlew :web:bootRun`

Then we can see this on terminal:
![image](https://user-images.githubusercontent.com/59259958/147989071-468c0dc1-0caf-43c7-a437-7d135a7c69b2.png)


And in `localhost:3333` we can see: 

![image](https://user-images.githubusercontent.com/59259958/147989109-a62f5c22-6403-48a9-83e6-7b0142333ed7.png)

- With all this running we can see on Eureka the services are registered: 

![image](https://user-images.githubusercontent.com/59259958/147989279-f4bbfab1-aabb-4d52-9121-6674d3a3409e.png)

### Second part 

- We modify the port in `\accounts\src\main\resources\aplication.yml` to 4444 for run other account. 
The terminal of this account: 

![image](https://user-images.githubusercontent.com/59259958/147989845-a4eae4af-76fb-4c68-b333-e711e126ef90.png)

And in `localhost:4444` we can see: 

![image](https://user-images.githubusercontent.com/59259958/147989920-a82187d7-fc68-4162-90b2-801b4cf1cb5c.png)

In Eureka we can see three services registered:

![image](https://user-images.githubusercontent.com/59259958/147990013-7036db78-41a8-48bd-8e7c-ca3447688963.png)


### Third part 

- After killing the account service in 2222, the corresponding service disappears from Eureka:

![image](https://user-images.githubusercontent.com/59259958/147990146-235d1843-09b0-4418-861f-f530bfa9e2ae.png)

 
 After that, you can ask information to the web service about the accounts without producing any 500: Internal Server Error.

This is what happens when asking for an account:  
![image](https://user-images.githubusercontent.com/59259958/147990456-94817b92-975f-4907-94b3-9b4054ad8b52.png)

Asking for details we can see:
![image](https://user-images.githubusercontent.com/59259958/147990476-31de0c5c-da5d-4bc1-9f02-947d5d310bb5.png)

After kill the service it still works beasuse when the web server is asked for an account it asked eureka where is located. 
It doesn't have a direct route to the account server instead it has one logic which is traslate bye eureka to the real one. 

