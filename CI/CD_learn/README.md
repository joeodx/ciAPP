# What is WebHook and how can we test it with github and jenkins 
*****************************

* A webhook is a way for one application to notify another application automatically when a certain event occurs.
* GitHub and Jenkins are both tools commonly used in software development, and they can be integrated using webhooks to automate various tasks,    such as triggering builds in Jenkins whenever code changes are pushed to a GitHub repository.


## Continuous intergration testing from localhost to jenkins 
 
 First of all what is a CI pipeline?

 * A Continuous Integration (CI) pipeline is a set of automated processes that software development teams use to build, test, and deploy their code changes. 
 * The primary goal of a CI pipeline is to automate the steps involved in integrating new code into a shared repository and ensuring that it functions correctly with the existing codebase.

  Lets looks at what this CI pipeline means belwo : 
 

![](CICD.png)

When is a CI pipeline used?
* CI pipelines are used whenever there are code changes to integrate into a project's codebase.
* Developers trigger CI pipelines by pushing code changes to a version control system (e.g., Git) or by creating pull requests.
* In our case looking at the diagram we are pushing the code automatically to jenkins to test the code before it is either deployed or delivered.

