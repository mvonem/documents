# Getting Started with Node.js

<!-- Inline <img src="/assets/nodejs-new-pantone-black.png" width=50> With Reference Link -->
## Introduction
This tutorial will have you deploying a Node.js app to ONEm in minutes.

The tutorial assumes that you have a free [ONEm account](http://testtool.dhq.onem:6060/), and that you have [Node.js](https://nodejs.org/), npm and [git](https://github.com/) installed locally.

## Choose a hosting platform

Your app will need to be hosted on the internet so that ONEm's servers can access it.  Choose a hosting provider.  

Hosting provider requirements:

* Public static IP or a permanent DNS host name
* Optional - access to local or cloud database services such as [PostgreSQL](https://www.postgresql.org/) or [MongoDB](https://www.mongodb.com/)

In general, ONEm apps can be hosted on any platform, it's entirely up to you which provider you use.

Some popular providers you might consider:

* [Heroku](https://www.heroku.com/)
* [DigitalOcean](www.digitalocean.com/)
* [Amazon Web Services (AWS)](https://aws.amazon.com/websites/)
* [Microsoft Azure](azure.microsoft.com/Account/Free‎)
 
## Set up

To use ONEm effectively, we recommend you install git.  Git is a popular version control system and will allow you to clone the examples and access our APIs.

* [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).  
* Run the [First-time setup steps](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

Before you continue, check that you have the prerequisites installed properly. Type each command below and make sure it displays the version you have installed. Your versions might differ from the example. If an error is returned, go back check the installation before continuing.

This tutorial will work for any version of Node greater than 8 - check that it’s there:

```
$ node --version
v10.13.0
```

npm is installed with Node, so check that it’s there. If you don’t have it, install a more recent version of Node:

```
$ npm --version
$ 6.9.0
```
Now check that you have git installed:

```
$ git --version
git version 2.15.1
```

## Prepare the app

In this step, you will prepare a simple **Hello World** application that’s ready to be deployed to ONEm.

To clone a local version of the sample application that you can then deploy to your hosting provider, execute the following commands in your local command shell or terminal:

```
$ git clone https://github.com/chrishornmem/hello-world.git
$ cd hello-world
```
You now have a functioning git repository that contains a simple application as well as a `package.json` file, which is used by npm (Node’s dependency manager).

## Install and Deploy your app

Make sure your app is deployed and running on your favourite provider.  For example to deploy on heroku would execute:

```
$ heroku create
$ git push heroku master
```

Install the package dependencies with npm:

```
$ npm install
```

## Configure the app

The **Hello World** example application by default listens on the HTTP port defined by the environment varible `PORT` or 8080 by default.

Make a note of the IP address or fully qualified URL of your application from your provider together with the port.  For example with heroku, it might be something like: https://example.herokuapp.com:8080 or with DigitalOcean it might be http://63.x.y.z:8080

## Run the app

Start the app with:

```
$ npm run start
```

You should see the following output:

```
Listening on port 8080
```

## Register the app with ONEm

If you have not already done so, sign-up for a free ONEm developer account [here](http://testtool.dhq.onem:6060/).

Register your app on the ONEm portal.  On the portal you will need to:

1. Give your app a unique name
2. Provide a description for your app.
3. Provide a link to your website
4. Provide the fully qualified URL+port to your app in the **CallBack URL** field

Don't worry about the other app details at this stage (verbs, permissions), we will use them later in the advanced tutorials.


## Test the app

Head over to our [sandbox](https://poc.onem.com).  In the input field, enter # followed by your app's name, for example **#HELLO** if you app is called Hello.

You should get back a MENU, similar to the below:

```
#HELLO WORLD
A First option
B Second option
C Third option
--Reply A-C
```

Congratulations, you have successfully installed your first app.  Give yourself a pat on the back and then head over to the advanced tutorials to get to know ONEm better.
