# DevOptics Value Streams
A CloudBees DevOptics Value Stream models a complex continuous delivery process and can be assembled from multiple pipelines. A Value Stream shows a series of interconnected gates or steps that deliver value to a customer. Those steps are presented in the "Value Stream view". The Value Stream view allows you to:

* Track changes
* Detect stalled and delayed changes
* Identify failures and blockages
* Find components ready for testing
* View contributing components

## Value Stream Mapping for Microservices
Using the two applications used in the CloudBees Core Pipelines Workshop, we will show how you can use DevOptics Value Streams to map the software delivery process of loosely coupled microservices as separated streams as part of a holistic value stream.

### Fork the **helloworld-api** repository.
The workshop utilizes the **helloworld-api** repository from the [CloudBees Days GitHub Organization](https://github.com/cloudbees-days). Fork the **helloworld-api** repository into the GitHub Organization that you created for the workshops (if you are not sure how to fork a repository - see this [GitHub Guide on forking](https://guides.github.com/activities/forking/)):

* https://github.com/cloudbees-days/helloworld-api

### Value Stream Visual Editor
DevOptics visual editor lets you model different phases and gates of your value stream.

* Phases - the milestones or stages used to deliver the software
* Gates - the Jenkins pipeline that is run to move the code change forward (e.g. build, test, deploy, …​)

Once modeled you can instrument your Jenkins Pipelines from the CloudBees Core Pipeline Workshop so DevOptics is able to track tickets and commits flowing through the value stream end to end.

1. Go back to DevOptics in your browser and switch to the **Value Streams** view and click on the **Create New** button in the upper right corner <p><img src="img/streams/value_streams_views.png" width=800/> This will open the [**Value Stream Visual Editor**](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#devoptics-visual-editor)
2. Click on the default title in the upper-left and change the title to be **{your GitHub username} helloworld** and hit return <p><img src="img/streams/change_title.png" width=800/>
3. Next click on the **Untitled Gate** below the **Build** phase and then click on the **cog** to configure the gate <p><img src="img/streams/configure_build_gate.png" width=500/>
4. Fill out the gate configuration form - **IMPORTANT: Replace `your GitHub username` with your GitHub username**:
  - **Gate Name**: development branch
  - **Master**: https://cje.workshop.beedemo.net/teams-`your GitHub username`/
  - **Job**: `your GitHub username`/helloworld-api/development
  - **Phase**: Build
  - leave the other fields as is <p><img src="img/streams/build_gate_form.png" width=500/>
  - **Save** the form
5. Click on the **Untitled Gate** below the **Test** phase, then click on the **cog** to configure the gate and fill out the gate configuration form:
  - **Gate Name**: test branch
  - **Master**: https://cje.workshop.beedemo.net/teams-`your GitHub username`/
  - **Job**: `your GitHub username`/helloworld-api/test
  - **Phase**: Test
  - leave the other fields as is 
  - **Save** the form
6. Click on the **Untitled Gate** below the **Release** phase, then click on the **cog** to configure the gate and fill out the gate configuration form:
  - **Gate Name**: master branch
  - **Master**: https://cje.workshop.beedemo.net/teams-`your GitHub username`/
  - **Job**: `your GitHub username`/helloworld-api/master
  - **Phase**: Release
  - Check the **This is a deployment job** checkbox <p><img src="img/streams/release_gate_form.png" width=500/>
  - **Save** the form
  7. Click on the **Save** button in the upper-left to save the Value Stream <p><img src="img/streams/save_value_stream.png" width=800/>

## DevOptics Performance Metrics
After you save your initial Value Stream, your instructor will commit a number of changes to the ***cloudbees-days/helloworld-api*** repository to simulate [DevOptics Performance metrics](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#_devops_performance_metrics).

TODO - Add explanations as changes are being processed
* Update the Jenkinsfile to fail and commit a change with a JIRA ticket id of **API-1001** 

### Value Stream JSON Editor

In addition to the Visual Editor, DevOptics also provides a JSON editor. The JSON editor is only available to update a Value Stream created by the Visual Editor.

1. Go back to DevOptics in your browser and switch to the **Value Streams** view and click on the **Create New** button in the upper right corner <p><img src="img/streams/value_streams_views.png" width=800/> This will open the [**Value Stream Visual Editor**](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#devoptics-visual-editor)
2. Click on the default title in the upper-left and change the title to be **{your GitHub username} Hello App**, hit return and then click the **Save** button in the upper-left to save the Value Stream<p><img src="img/streams/json_change_title.png" width=800/>
3. Next, click on the the 3 vertical dots next to the ***Seach by Ticket Id*** and select **Edit JSON** from the menu <p><img src="img/streams/edit_json.png" width=800/>
4. Delete the **Value Stream JSON** content and replace with the following:
```
{
	"phases": [
		{
			"id": "TSlZ0sqDuh",
			"name": "Build",
			"gates": [
				{
					"id": "5eMvajavv",
					"name": "API Dev",
					"master": "https://cje.workshop.beedemo.net/teams-beedemo-dev/",
					"job": "beedemo-dev/helloworld-api/development",
					"feeds": "v-4fcgpTY"
				},
				{
					"id": "ZF5Ou-7vv",
					"name": "UI Dev ",
					"master": "https://cje.workshop.beedemo.net/teams-beedemo-dev/",
					"job": "beedemo-dev/template-jobs/beedemo-dev-hello/development",
					"feeds": "release"
				}
			]
		},
		{
			"name": "Test",
			"id": "QLggEt9hI",
			"gates": [
				{
					"id": "v-4fcgpTY",
					"name": "API Test",
					"master": "https://cje.workshop.beedemo.net/teams-beedemo-dev/",
					"job": "beedemo-dev/helloworld-api/test",
					"feeds": "yiK5MUR5Q"
				}
			]
		},
		{
			"name": "Deploy API",
			"id": "ExwDnpexcA",
			"gates": [
				{
					"id": "yiK5MUR5Q",
					"name": "API Master",
					"master": "https://cje.workshop.beedemo.net/teams-beedemo-dev/",
					"job": "beedemo-dev/helloworld-api/master",
					"feeds": "release",
					"type": "deployment"
				}
			]
		},
		{
			"name": "Deploy App",
			"id": "8THbC9EXqX",
			"gates": [
				{
					"id": "release",
					"name": "UI Master",
					"master": "https://cje.workshop.beedemo.net/teams-beedemo-dev/",
					"job": "beedemo-dev/template-jobs/beedemo-dev-hello/master",
					"type": "deployment",
					"feeds": null
				}
			]
		}
	]
}
```
5. Replace all occurences of **beedemo-dev**, both for the `master` value and the `job` value, in the JSON with your GitHub username.
6. Click the **Save changes** button <p><img src="img/streams/save_json.png" width=800/>
7. You will have a new Value Stream and the **API Master** gate should already have tickets in it <p><img src="img/streams/api_gate.png" width=800/>

### Fix Your **helloworld-nodejs** Application

Before you fix your fork of the **helloworld-nodejs** repostiory we will run it again by making a simple change and commiting it on your **development** branch. 

1. Open the GitHub editor for the `Jenkinsfile` file in the **development** branch of your forked **helloworld-nodejs** repository, add a blank line at the bottom and then commit the change to the **development** branch with the commit message ***UI-1001 still broken***
2. Once again, your **[GitHub username]-hello** Multibranch **development** job should run and fail and in DevOptics you should see that the **UI Dev** gate has 1 ticket in it and that it failed
3. Now we will fix your app. Open the GitHub editor for the `hello.js` file in the **development** branch of your forked **helloworld-nodejs** repository, on line 13 fix the misspelled ***Worlld*** and then commit the change to the **development** branch with the commit message ***UI-1001 fixed misspelling***
4. Now your job should complete successfully and the **UI Dev** gate should show that it finished successfully - what is your MTTR for the **UI Dev** gate? What is the MTTR for the entire Value Stream?
5. Now that you have fixed your **helloworld-nodejs** application it is time to merge to the **master** branch and deploy. Create a [Pull Request](https://help.github.com/en/articles/creating-a-pull-request) between the **development** branch and **master** branch of your forked **helloworld-nodejs** repository. 
6. Changed the **base repository** to the **master** branch of your forked **helloworld-nodejs** repository (not the **cloudbees-days** repository), add a comment and then click the **Create pull request** button 
7. A job will be created for the pull request and once it has completed successfully your pull request will show that **All checks have passed**. Go ahead and click the **Merge pull request** button and then click the **Confirm merge** button but DO NOT delete the **development** branch
8. In your DevOptics Value Stream you should see the **UI-1001** ticket move from the **UI Dev** gate to the **UI Master** gate. What is your deployment frequency?

