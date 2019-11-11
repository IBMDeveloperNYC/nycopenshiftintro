# OpenShift on IBM Cloud Workshops

[Red Hat OpenShift on IBM Cloud](https://cloud.ibm.com/docs/openshift?topic=openshift-why_openshift) is an extension of the IBM Cloud Kubernetes Service, where IBM manages OpenShift Container Platform for you. 

With Red Hat OpenShift on IBM Cloud developers have a fast and secure way to containerize and deploy enterprise workloads in Kubernetes clusters. OpenShift clusters build on Kubernetes container orchestration that offers consistency and flexibility for your development lifecycle operations.

This repository holds a series of workshops that help you as a developer to become familiar with Red Hat OpenShift, how it can be deployed on the IBM Cloud, and how to deploy applications on and with OpenShift.

In order to run these workshops, you need an [IBM Cloud account](https://ibm.biz/BdzCzv).

## Workshop 1: Understanding OpenShift

In this workshop we will show you how to create your own OpenShift cluster on the IBM Cloud, how to use the `oc` CLI (command line interface) and how to use the OpenShift Web Console to deploy applications.

* Duration: 60 - 90 minutes
* Audience: Beginner

This workshop has been adapted from [this repository](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops).

## Part 1: Introduction

Our colleague Sai Vennam, IBM Cloud Developer Advocate, has created two videos about OpenShift on the IBM Cloud that you should watch:

#### Intro to Red Hat OpenShift on IBM Cloud

[![Intro to Red Hat OpenShift on IBM Cloud](http://img.youtube.com/vi/hdwDMsDF9J8/0.jpg)](http://www.youtube.com/watch?v=hdwDMsDF9J8 "Intro to Red Hat OpenShift on IBM Cloud")

What is OpenShift? OpenShift on the IBM Cloud is a fully managed offering, with multiple deployment options, and certification. It is a Unified Hybrid Cloud platform.

#### Guided Tour for Red Hat OpenShift on IBM Cloud

[![Guided Tour for Red Hat OpenShift on IBM Cloud](http://img.youtube.com/vi/l4Vrj7mkxhQ/0.jpg)](http://www.youtube.com/watch?v=l4Vrj7mkxhQ "Guided Tour for Red Hat OpenShift on IBM Cloud")

How to create an OpenShift cluster in IBM Cloud, how to create a project in the OpenShift Web Console.

## Part 2: Create an OpenShift Cluster on the IBM Cloud

#### How it usually looks:

[video (3:16 mins)](http://www.youtube.com/watch?v=9xgqDP2B3WI)

#### Special Process for Us Today:

1. Make sure you've created your IBM Account. If you haven't yet, please use the following link: https://ibm.biz/BdzCzv
2. Navigate to https://nycopenshift.mybluemix.net
3. Use the key for this event :   `oslab`
4. Select the US East Region

Your completed screen should resemble what's below:

![checkedWelcome](images/checkedWelcome.png)


After submitting, you should see a screen similar to the following image:

![congrats](images/congrats.png)


Log in to your cloud account and have a look at your dashboard. In the dropdown where your name is displayed, select 1840867 - IBM

![dashboard](images/dashboard.png)


Select "Clusters" and click on your cluster that was assigned to you when you submitted your credentials:

![dashboard2](images/dashboard2.png)


You should be taken to the page for your cluster which will resemble the page below:

![cluster dashboard](images/osCloud.png)



## Part 3: Red Hat Tutorials (Optional)

Ordinarily, there would be some downtime between the creation of your OpenShift cluster and your ability to access it. Since we've already done this ahead of time, you can log right on and start working with it. If you'd like a safe test environment to learn about OpenShift, there is a lot of really good material at the Red Hat OpenShift [Interactive Learning Portal](https://learn.openshift.com/). You get access to a real OpenShift system during these tutorials.

We will be going through at least a couple of these on the actual clusters in Part 4.

1) [Getting Started with OpenShift for Developers](https://learn.openshift.com/introduction/getting-started/):
In this tutorial you will learn the fundamentals:
   * Basics of the OpenShift platform and the Learning Portal environment (Katacoda)
   * Using the `oc`CLI and the Web Console
   * What is a project? Creating a project in OpenShift
   * Deploying an app from a Docker image
   * Scaling an app, self-healing
   * What is a Route? Creating a Route
   * Using Source-to-Image to create an app


2) [Deploying Applications From Images](https://learn.openshift.com/introduction/deploying-images/):
This tutorial is about deploying an application from an existing image (from Docker Hub) and how OpenShift creates a deployment on Kubernetes without the developer touching any YAML files. It includes:

   * Creating a Projects
   * Deploy a Docker image from the Web Console
   * Create an external Route
   * Delete an application (everything) from the command line using labels
   * Deploy a Docker image from the command line
   * Import an application image, work with image streams


3) [Deploying Applications From Source](https://learn.openshift.com/introduction/deploying-python/):
This tutorial uses a code repository on Github that holds a Python application. The Source-to-Image builder uses a Python template from the OpenShift catalog to create a Container image within OpenShift and deploys it, again without the developer touching any YAML files. Another method, binary build, creates the image from code on the developers workstation. These are the topics of this tutorial:  
   * Create a Project
   * Source-to-Image (S2I) of a Python project in Github
   * Builder Logs
   * Accessing the application
   * Deleting the application via CLI
   * S2I via `oc`command line, differences to Web Console
   * Triggering a new build
   * Binary build from a local code repository

## Part 4: Deploy an application on OpenShift on the IBM Cloud

The setup of the OpenShift cluster must be completed to finish this workshop. It is completely set up when the worker node(s) show a status of "Normal" in the "Worker Nodes" section __AND__

![OS Create 1g](images/os_worker_rdy.png)

if there is a "Ingress subdomain" displayed in the "Overview" of the cluster:

![OS Create 1g](images/os_worker_rdy3.png)

Access the OpenShift Web Console via the button (1) in this dialog. 

![OS Webconsole](images/os_webconsole.png)

You have seen and used this Web Console in the interactive tutorials in Part 3. But notice the User ID (1) and the down arrow to right of it. If you click on it you will see an important option: "Copy Login Command". This allows you to login to your OpenShift cluster on IBM Cloud with the `oc`CLI. But first you need to install the CLI.

This part of the workshop is divided in two sections:

  A. Working with the OpenShift Web Console 
  
  B. Working with the `oc`command line tool


### A. Deploy an application from the Web Console

1. In the OpenShift Web Console, click "+ Create Project" and give your project a name, e.g. "blog". Click "Create".

2. Click on your new project "blog" in the "My Projects" list. This opens the projects Overview, which is empty and offers you some "Get started" options.

![OS Project Overview](images/os_project_overview.png)

3. Click on "Deploy Image".

4. Select "Image Name" and enter `openshiftkatacoda/blog-django-py` as name, then click on the "magnifying glass". 

![OS Deploy 1](images/os_deploy_1.png)

5. OpenShift reads details from the image and displays them. It fills in a name, based on the image name, and a label "app" whose content is also based on the image name. 

![OS Deploy 2](images/os_deploy_2.png)

6. Leave the defaults and click "Deploy". In the resulting dialog click the "Continue to the project overview" link.

![OS Deploy 3](images/os_deploy_3.png)

7. In the project overview, click on the twistie (1) to open the overview of the application. This example should be familiar, it was used in the second tutorial on the Red Hat Learning portal.
Create a Route (2), accept the defaults, and click on the resulting URL. The blog application should open.
If you want, scale the deployment up and down (3). 

![OS Deploy 4](images/os_deploy_4.png)

### B. Deploy an application with `oc` from the command line 

The OpenShift `oc` command line tool includes all the functionality of the Kubernetes native `kubectl` CLI but it has also all the function required for OpenShift specifics, e.g. a `login` command to access the OpenShift cluster.

### Install the OpenShift `oc` CLI

Go back to the IBM Cloud Dashboard and display your OpenShift cluster. If you closed the IBM Cloud Dashboard you can find OpenShift clusters [here](https://cloud.ibm.com/kubernetes/clusters?platformType=openshift).

In the "Access" section of your cluster is detailed information about installing the `oc`CLI and and the different methods to get access to your cluster.

![OS Access](images/os_access.png)

### Login to the OpenShift Cluster

Once `oc` is installed, copy the login command from the OpenShift Web Console and paste it into a command window (shell). It will look similar to this:

```
$ oc login https://c100-e.us-south.containers.cloud.ibm.com:30*** --token=z5cuqxABC-9QdqE1ivXYZ1z_Y6Tghj1qxN-abCWc1Bg
```

If login is successfull you will see all the projects on OpenShift that you have access to. 

Keep the command line open but go back to the OpenShift Web Console.

### Working with the `oc` CLI


1. Go back to your command line where you used `oc`to logon to your OpenShift cluster.

2. Switch to the project you created in the Web Console with:

```
$ oc project blog

Now using project "blog" on server "https://c100-e.us-south.containers.cloud.ibm.com:30***".
```

3. Display all objects that belong to your project:

```
$ oc get all -o name

pod/blog-django-py-1-qk7d9
replicationcontroller/blog-django-py-1
service/blog-django-py
deploymentconfig.apps.openshift.io/blog-django-py
imagestream.image.openshift.io/blog-django-py
route.route.openshift.io/blog-django-py
```

4. Display all objects that are labeled with your app name, the list should be the same as before:

```
$ oc get all -l app=blog-django-py -o name

pod/blog-django-py-1-qk7d9
replicationcontroller/blog-django-py-1
service/blog-django-py
deploymentconfig.apps.openshift.io/blog-django-py
imagestream.image.openshift.io/blog-django-py
route.route.openshift.io/blog-django-py
```

5. Delete them with:

```
$ oc delete all -l app=blog-django-py -o name

pod/blog-django-py-1-qk7d9
replicationcontroller/blog-django-py-1
service/blog-django-py
deploymentconfig.apps.openshift.io/blog-django-py
imagestream.image.openshift.io/blog-django-py
route.route.openshift.io/blog-django-py
```

   If you go back to the Web Console you should see that it updated the Overview which now should be empty again.

### Deploy an application from the command line

1. Check if the image is available:

```
$ oc new-app --search openshiftkatacoda/blog-django-py

Docker images (oc new-app --docker-image=<docker-image> [--code=<source>])
-----
openshiftkatacoda/blog-django-py
  Registry: Docker Hub
  Tags:     latest

```

2. Deploy the image as an application:

```
$ oc new-app openshiftkatacoda/blog-django-py

--> Found Docker image 927f823 (2 months old) from Docker Hub for "openshiftkatacoda/blog-django-py"

    Python 3.5 
    ---------- 
    Python 3.5 available as container is a base platform for building and running various Python 3.5 applications and frameworks. Python is an easy to learn, powerful programming language. It has efficient high-level data structures and a simple but effective approach to object-oriented programming. Python's elegant syntax and dynamic typing, together with its interpreted nature, make it an ideal language for scripting and rapid application development in many areas on most platforms.

    Tags: builder, python, python35, python-35, rh-python35

    * An image stream tag will be created as "blog-django-py:latest" that will track this image
    * This image will be deployed in deployment config "blog-django-py"
    * Port 8080/tcp will be load balanced by service "blog-django-py"
      * Other containers can access this service through the hostname "blog-django-py"

--> Creating resources ...
    imagestream.image.openshift.io "blog-django-py" created
    deploymentconfig.apps.openshift.io "blog-django-py" created
    service "blog-django-py" created
--> Success
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose svc/blog-django-py' 
    Run 'oc status' to view your app.
```

3. Check the status of your deployment:

```
$ oc status --suggest

In project blog on server https://c100-e.us-south.containers.cloud.ibm.com:30634

svc/blog-django-py - 172.21.51.187:8080
  dc/blog-django-py deploys istag/blog-django-py:latest 
    deployment #1 deployed 56 seconds ago - 1 pod

Info:
  * dc/blog-django-py has no readiness probe to verify pods are ready to accept traffic or ensure deployment is successful.
    try: oc set probe dc/blog-django-py --readiness ...
  * dc/blog-django-py has no liveness probe to verify pods are still running.
    try: oc set probe dc/blog-django-py --liveness ...

```

The --suggest options even gives you infos on things that are missing in your configuration.

4. Your application needs a Route to expose it externally:

```
$ oc expose service/blog-django-py

route.route.openshift.io/blog-django-py exposed
```

5. Display the URL of the Route:

```
$ oc get route/blog-django-py

NAME             HOST/PORT                                                                                                               PATH      SERVICES         PORT       TERMINATION   WILDCARD
blog-django-py   blog-django-py-blog.harald-uebele-openshift-5290c8c8e5797924dc1ad5d1bcdb37c0-0001.us-south.containers.appdomain.cloud             blog-django-py   8080-tcp                 None
```

You can see the very long URL. If you want, copy it and open it in your browser.

6. Cleanup. This deletes everything including your project!
   This command takes a while to complete.

```
$ oc delete project blog

project.project.openshift.io "blog" deleted
```
You can also delete a complete project from the Web Console.

---


Congratulations! You have completed this workshop!  
