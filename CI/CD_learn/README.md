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

# Deploying our app via jenkins master server 

1. Log into jenkins. 

2. Add a description to your project and then select the Github project checkbox and add your projects Url.
   For example mine was : 
```
git@github.com:Ziziou91/tech258_cicd.git
```

![](/images/sc.jpg)

3. Go to the office 365 connector and click the option that says **Restrict where this project can be run**. Then under **label expression** add ```sparta-ubuntu-app```


4. On the **source managment tab** slect Git. Add the the github repo URL. You should have already have your SSH key set up so you should get a error message now. 

5. To fix this, add your private ssh key for the repo to Jenkins, and then choose it in the credentials. 

6. Also **change the branch to main** like below : 

![](/images/sc2.jpg)


7. Now we need to provide a Node and npm for our app. Under the build environment tab cchec



