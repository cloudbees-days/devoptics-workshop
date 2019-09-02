# CloudBees DevOptics Workshop
This workshop will provide a basic understanding of how to create Value Streams, monitor the Platform at scale and continually measure DevOps performance leveraging features of [CloudBees DevOptics](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/). 

This repository contains instructions and learning materials for the workshop that is designed to teach the following key concepts:

  * How specific features of CloudBees DevOptics allows organizations to measure, analyze and accelerate [DevOps performance](https://www.cloudbees.com/resource/whitepaper/devops-performance-importance-measuring-throughput-and-stability)?
  * Benefits of using CloudBees DevOptics [Value Streams](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#_value_stream_concepts) in concert with [Jenkins Pipelines](https://jenkins.io/doc/book/pipeline/syntax/#declarative-pipeline)? 
  * How to create [reusable templates for Value Streams](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/value_streams/#devoptics-value-stream-template-microservices)?
  * How CloudBees DevOptics [Run Insights](https://go.cloudbees.com/docs/cloudbees-documentation/devoptics-user-guide/run_insights/#_run_insights_concepts) provides a comprehensive view of the status of your CD platform and software delivery pipelines?

To get started goto the [**Setup Instructions**](Setup.md).

# Workshop Prerequisites

In order to follow along with the hands on portion of the workshop students should have the following resources available to them:

  * Internet access to include access to https://github.com to include the ability to access and use [the GitHub File Editor](https://help.github.com/articles/editing-files-in-your-repository)
  * A basic understanding of Jenkins Pipelines: https://jenkins.io/doc/book/pipeline/getting-started/ 

The setup guide will walk students through:
  * Creating an account on https://github.com and a basic understanding of how to use GitHub to do things like fork a repository, edit files in the web UI, and create pull requests
  * Creating a personal access token for your Github account with the following permissions:
    - repo: all
    - admin:repo_hook: all
    - admin:org_hook
    - user: all
   
Detailed setup instructions are available at **[Setup](Setup.md)**

# Workshop Labs

**The labs covered in this workshop are available at the following links:**

* Lab 1. [Introduction to Value Streams using CloudBees DevOptics](./value-streams.md)
* Lab 2. [Measure DevOps Performance with Value Streams](./value-streams-measurement.md)
* Lab 3. [Value Stream as Code](./value-streams-as-code.md)
* Lab 4. [Platform Monitoring using DevOptics Run Insights](./insights.md)

# Disclaimer

Although the examples and code in this repository was originally created by employees of CloudBees, Inc. to use in training customers, your use of this material is not sponsored or supported by CloudBees, Inc.

# Contributors 

* Contributors: [Kurt Madel](https://github.com/kmadel), [Anand Chauhan](https://github.com/anandcpm)
 
# Questions, Feedback, Pull Requests Etc.

If you have any questions, feedback, suggestions, etc. please submit them via issues or, even better, submit a Pull Request!
