# DevOptics Value Streams
A CloudBees DevOptics Value Stream models a complex continuous delivery process and can be assembled from multiple pipelines. A Value Stream shows a series of interconnected gates or steps that deliver value to a customer. Those steps are presented in the "Value Stream view". The Value Stream view allows you to:

* Track changes
* Detect stalled and delayed changes
* Identify failures and blockages
* Find components ready for testing
* View contributing components

## Value Stream Editor
DevOptics visual editor lets you model different phases and gates of your value stream.

* Phases - the milestones or stages used to deliver the software
* Gates - the Jenkins pipeline that is run to move the code change forward (e.g. build, test, deploy, …​)

Once modeled you can instrument your Jenkins Pipelines from the CloudBees Core Pipeline Workshop so DevOptics is able to track tickets and commits flowing through the value stream end to end.

### Value Stream Mapping for Microservices
Using the two applications that we created Pipelines for in the CloudBees Core Pipelines Workshop we show how you can use DevOptics Value Streams to map the software delivery process of loosely coupled microservices as separated streams as part of a holistic value stream