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

# Deploying our app via jenkins master server with automated testing and webhook
************************************

1. Log into jenkins. 

2. Add a description to your project and then select the Github project checkbox and add your projects Url.
   For example mine was : 
```
git@github.com:Ziziou91/tech258_cicd.git
```

![](/imagessc.jpg)

3. Go to the office 365 connector and click the option that says **Restrict where this project can be run**. Then under **label expression** add ```sparta-ubuntu-app```


4. On the **source managment tab** slect Git. Add the the github repo URL. You should have already have your SSH key set up so you should get a error message now. 

5. To fix this, add your private ssh key for the repo to Jenkins, and then choose it in the credentials. 

6. Also **change the branch to main** like below : 

![](/images/sc2.jpg)


7. Now we need to provide a Node and npm for our app. Under the build environment check Provide Node and npm bin? folder to Path.
  Change the node installation to ``Sparta-Node-JS```

8. When you go to build tab add this to the execute shell : 


```
cd
cd npm install
npm test 
```

![](/images/done.jpg)


9. Now save this. Our jenkins Master should be set up now.

10. Now head to your github repp and go to the setting called webhooks. You see an option callled called paylaod, make sure to enter the url for the jenkins serve like below : 

 * and the content type is **application/json**
 * click **jsut the push event**
 * click **Active**


![](/images/3.jpeg)

Then click update webhook. The webhook will send a post HTTP request to our jenkins server. **200** if is correct and **404** if not

11. Now go back to the jenkisn config page for our job and under the build triggets tab, make sure to check **Github hook triggers for GITScm polling. 

***************************************************

## CI pipelines with jenkins and GIThub
*************************************

* You should never code on your main branch. Code on a dev branch or a seperate branch from main.

1. Create a dev branch using ```git checkout``` in your local repositry
2. For testing purposes, make a change to your work. 
3.  Now using the testing job we created before, if the test pass it shall trigger the next job to merge the code from your new branch you created to ```main```
  

## Continus Delivery with Jenkins 

* Now our code has been tested and has merged to the ```main branch``, the next step is to copy that code over to production
* In our case that will be a ec2 instance. 

How do we do this?

1. Create a EC2 instance on AWS- with **Ubuntu 18.04 LTS**
2. Configure the network security group to allow *ssh*,**3000**(node app) and 8080(for jenkins)
3. git clone the app coide to the EC2 instance we made.
4. Install what dependencies are required.

* Once this is done we can now ssh into the instancew we made and manually install and start the app

## Continious Deployment with Jenkins 

How do we get our code to automatically deployed to the cloud?

1. Use jenkins to ssh into our EC2 without user input so add the ```frontend command```
2. Head to the app folder.
3. start the app in the background!

***************************************************************



