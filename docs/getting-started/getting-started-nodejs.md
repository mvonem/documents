# Getting Started with Node.js

<!-- Inline <img src="/assets/nodejs-new-pantone-black.png" width=50> With Reference Link -->
## Introduction
This tutorial will have you deploying a Node.js app to ONEm in minutes.

The tutorial assumes that you have a free [ONEm account]({{links.portal}}), and that you have the following prerequisites installed locally:

* [Node.js](https://nodejs.org/)
* npm which is installed with Node.js
* [git](https://github.com/)
* [ngrok](https://ngrok.com/download)

## Set up on localhost

To start with, we will be running all commands locally on your own PC.  Your app will initially be hosted there for local development, then later you will learn how to host your app with a hosting provider for use on production.

Before you continue, check that you have the prerequisites installed properly. Type each command below and make sure it displays the version you have installed. Your versions might differ from the example. If an error is returned, go back check the installation before continuing.

This tutorial will work for any version of Node greater than 8 - check that it’s there:

```bash
$ node --version
v10.15.3
```

npm is installed with Node, so check that it’s there. If you don’t have it, install a more recent version of Node:

```bash
$ npm --version
6.9.0
```
Now check that you have git installed:

```bash
$ git --version
git version 2.15.1
```

We will use *ngrok* to provide a secure tunnel between your app running on *localhost* and the ONEm servers. Check it's installed:

```bash
$ ./ngrok --version
ngrok version 2.3.29
```

## Prepare the app

In this step, you will prepare a simple *Hello World* application.  To clone a local version of the sample application, execute the following command in your local command shell or terminal:

```bash
$ git clone https://github.com/chrishornmem/hello-world.git && cd hello-world
```

You now have a functioning git repository that contains the *Hello World* application as well as a `package.json` file, which is used by npm (Node’s dependency manager).

Install the package dependencies with npm:

```bash
$ npm install
```

## Configure the app

The *Hello World* example application listens on the HTTP port defined by the environment variable `PORT` or 8080 by default.  You can change the port by creating a `.env` file in your app's root directory and specifying the desired port value:

```
PORT=8080
```

## Run the app

Start the app with:

```bash
$ npm run start
```

You should see output similar to the following in the console:

```
Listening on port 8080
```

Now run ngrok so that your app is visible to the ONEm servers.

```
$ ./ngrok http 8080
```

ngrok will launch a continuous display to the console.  Make a note of the http or https forwarding address.  In the example below the address is `http://6e3f3fce.ngrok.io`:

```
Forwarding                    http://6e3f3fce.ngrok.io -> http://localhost:8080
```

Navigate to the forwarding link on your browser and you should see a *Hello World* greeting.

The *Hello World* example application will wait for HTTP callback requests as users send SMS messages.  The sample app expects to receive callbacks on the base path: `/api`.  The ONEm servers need to know the fully qualified URL for your app, including the base path.  In our example above, the *Callback URL* would be `http://6e3f3fce.ngrok.io/api`

Make a note of your *Callback URL*, you will need it in the next step.

## Register the app with ONEm Sandbox Portal

If you have not already done so, sign-up for a free ONEm developer account on the sandbox [here]({{links.portal}}).

Register your app on the ONEm Sandbox Portal.  You will need to provide:

1. A unique one-word name for your app, e.g *hello*
2. A description of your app
3. A link to your website
4. The *Callback URL* you obtained from the previous step

Don't worry about the other app details at this stage (verbs, permissions), we will use them later in the advanced tutorials.

Make sure the details are saved correctly in the portal.


## Test the app

Head over to our [sandbox test tool](https://poc.onem.com), we call it *ONEm Zone*.  Sign-up and then in the input field, enter `#` followed by your app's name, for example `#HELLO` if your app is called *hello*.

The ONEm system should respond with a menu, similar to the below:

```
#HELLO WORLD
A First option
B Second option
C Third option
--Reply A-C
```

Congratulations, you have successfully installed your first app.  Give yourself a pat on the back and then head over to the advanced tutorials to get to know ONEm better.

## Running your app in production

### Choose a hosting platform

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

### Install and deploy your app on production

Make sure your app is deployed and running on your favourite provider.  For example to deploy on heroku you would use:

```bash
$ heroku create
$ git push heroku master
```

Make a note of the IP address or fully qualified URL of your application from your provider together with the port.  For example with heroku, it might be something like: `https://example.herokuapp.com:8080` or with DigitalOcean it might be `http://63.x.y.z:8080`

### Register the app with ONEm Production Portal

In the *Callback URL* field, provide the fully qualified URL of your application's base API path.

### Verifying on production

Head over to our production verification site [onem.zone](https://onem.zone) and verify that your app is responding as expected.
