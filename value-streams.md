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

1. Go back to DevOptics in your browser and switch to the **Value Streams** view and click on the **Create New** button in the upper right corner <p><img src="img/streams/value_streams_views.png" width=800/> This will open the [**Value Stream Visual Editor**](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#devoptics-visual-editor)
2. Click on the default title in the upper-left and change the title to be **{your GitHub username} helloworld-api** and hit return <p><img src="img/streams/change_title.png" width=800/>
3. Next click on the **Untitled Gate** below the **Build** phase and then click on the **cog** to configure the gate <p><img src="img/streams/configure_build_gate.png" width=800/>
4. Fill out the gate configuration form:
  - **Gate Name**: development branch
  - **Master**: https://cje.workshop.beedemo.net/teams-beedemo-dev/
  - **Job**: beedemo-dev/helloworld-api/development
  - **Phase**: Build
  - leave the other fields as is <p><img src="img/streams/build_gate_form.png" width=800/>
  - **Save** the form
5. Click on the **Untitled Gate** below the **Test** phase, then click on the **cog** to configure the gate and fill out the gate configuration form:
  - **Gate Name**: test branch
  - **Master**: https://cje.workshop.beedemo.net/teams-beedemo-dev/
  - **Job**: beedemo-dev/helloworld-api/test
  - **Phase**: Test
  - leave the other fields as is 
  - **Save** the form
6. Click on the **Untitled Gate** below the **Release** phase, then click on the **cog** to configure the gate and fill out the gate configuration form:
  - **Gate Name**: master branch
  - **Master**: https://cje.workshop.beedemo.net/teams-beedemo-dev/
  - **Job**: beedemo-dev/helloworld-api/master
  - **Phase**: Release
  - Check the **This is a deployment job** checkbox <p><img src="img/streams/release_gate_form.png" width=800/>
  - **Save** the form
  7. Click on the **Save** button in the upper-left to save the Value Stream <p><img src="img/streams/save_value_stream.png" width=800/>

### Value Stream Mapping for Microservices
Using the two applications that we created Pipelines for in the CloudBees Core Pipelines Workshop we show how you can use DevOptics Value Streams to map the software delivery process of loosely coupled microservices as separated streams as part of a holistic value stream