# What is WebHook and how can we test it with github and jenkins 
*****************************

* A webhook is a way for one application to notify another application automatically when a certain event occurs.
* GitHub and Jenkins are both tools commonly used in software development, and they can be integrated using webhooks to automate various tasks,    such as triggering builds in Jenkins whenever code changes are pushed to a GitHub repository.


## Continuous intergration testing from localhost to jenkins 
 
 # First of all what is a CI pipeline?

 * A Continuous Integration (CI) pipeline is a set of automated processes that software development teams use to build, test, and deploy their code changes. 
 * The primary goal of a CI pipeline is to automate the steps involved in integrating new code into a shared repository and ensuring that it functions correctly with the existing codebase.

  Lets looks at what this CI pipeline means belwo : 
 

![](CICD.png)

When is a CI pipeline used?
* CI pipelines are used whenever there are code changes to integrate into a project's codebase.
* Developers trigger CI pipelines by pushing code changes to a version control system (e.g., Git) or by creating pull requests.
* In our case looking at the diagram we are pushing the code automatically to jenkins to test the code before it is either deployed or delivered.

How does a CI pipeline work?
* When triggered, a CI pipeline retrieves the latest code changes from the version control system and executes predefined stages or tasks
* Each stage in the pipeline performs a specific action, such as compiling code, running tests, checking code quality, or deploying artifacts.
* In our case the pipeline is being triggered when code needs to be teseted in Jenkins 
  
Why use a CI pipeline?
* There are many uses to a Ci pipeline. It saves time as you can automate the process of thigns you can do manually 
* It ensures consistency along how code gets built, tested or even deployed 
  ********************************



# What is a web hook?

* A webhook is a mechanism for automatically triggering an action or notifying an external system when a certain event occurs.

* An example of this would be on Amazing when you add an item to the basket it is checking first is that item in stock? If yes allow the item to be added to the basket. Then at the payment stage has the payment gone through? If yes send an email to notify the user of this. Has the item then been sent out for delivery? If yes notify the user that their item is on it's way.

* A webhook is what allows all of these actions to me automated without this it wouldn't feasibly be possible for someone to do this for the billions of orders amazon gets each year.

***********************************