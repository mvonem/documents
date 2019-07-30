<!-- Introduction should let user know about: -->

# What is ONEm Platform

ONEm has created a global multi-service Platform that provides innovative services using core connectivity as SMS and Voice. We provide first of a kind interactive services and user generated content on the mobile. It’s not about replacing or even competing with the internet, it’s all about taking what already exists and putting it to a better use.
ONEm allows people to communicate in a completely new way through simple interaction with an intelligent platform that works on their behalf behind the scenes to connect, find, process and present communications, content and services across all types of networks and to any type of mobile device.
Whether accessed through SMS or a web browser, the ONEm Platform manages user's identities and profile, delivers intelligent content and allows users to collaborate and interact in an unconventional way.

## Mission and vision

We are building a Mobile Ecosystem first of a kind with interactive services, that will transform the way people communicate and get access to information on any mobile, including the 3 billion people who have no access to internet, who have no way to share nor create their own content. We aim to provide access to information and to make our services available to everyone.
<!-- to add more -->

## How services work

ONEm's goal is to have a service that is easy and intuitive to use. It is important for users to have a seamless experience when accessing the ONEm platform.
Different functionalities and content types are grouped in applications, also called services, accessible through the Platform, similar to websites via internet. Each service is defined by a unique name, similar to a web-address, and follows a general structure, allowing users to easily interact with the platform via text messages.
Similar to a website, the application will have a landing page and will provide a navigation structure using menus, selectable outlines, paging mechanism and the possibility to capture user input.

To access a certain application/service, users will use # before application name, eg #my_application. The Platform will automatically recognise the user input and will display the application's landing screen. Usability principles are implemented, so in case of an unrecognised user input, the Platform will respond with the best feedback or guideline.

To allow us to create an ecosystem, the users will be automatically registered when sending their first message to the platform. Their profile will be created and based on setup they will be able to access the available applications. Obviously, an opt out mechanism is in place.


### Let's dig further into the anatomy of a ONEm application

Before dissecting the structure of applications, keep in mind that SMS does not facilitate the use of images or media files as web does. Though ONEm applications work also over internet, we offer users the same experience and interface.

A standard SMS is 140 8bit characters. For full compatibility the applications should display the information to the users in one SMS.
<!-- Since smart phones can display up to 5 messages, we offer the possibility to each user to change the acceptable size of the SMS they are willing to receive at one time using 'size' setting. -->

As explained in the previous section, the web-address is transposed to #application_name.
A website/web application provides pages, navigation system, hints and, most important, content. Let's see how those are translated to a ONEm application.

Every response message from ONEm Platform will have the following structure:
**HEADER** - each messages will have a header that indicates the name of the application and the section of the displayed content. This will allow users to get localised into the application serving as page title and/or breadcrumbs.
**BODY** - the body is the most important section of the message and handles the content being displayed to the user. It may consist of text, outline or selectable options. The end of the body will have the number of chunks remaining in the content selection. Will explain the chunks later on. The body can display an **OPTIONS** list, a simple text or a **FORM** step.
**FOOTER** - the footer is where information like 'hints' is attached to the bottom of the message. In here, users will find guidelines regarding next available actions.

All this might be more intuitive with an example from #onem application:
```
#ONEM MENU
A My account
B Invite friends to chat
C Create SMS group chats (xGroup)
D Services
E How to use
--Reply A-E
```
The above message is the landing page of #onem application, also considered the main menu. The first message presents user with the main options that can be accessed and offers a navigation possibility.
As you probably figured out, the user can access account information, chat with friends, see available services or follow a tutorial on how to use ONEm features. Each available option has a letter attached to it to facilitate user response. As hinted in the footer, the user can sent one of the letters to access the corresponding section. This is the **OPTIONS** concept. Each option is displayed on a new line and has associated an action to it that will result in another message displayed to the user.

Let's follow on the example and say that user will choose to reply to ONEm Platform with a message containing ```D``` letter. This translates in choosing to access section D, available services and the Platform's response will be a list of available service categories. Notice the header changed and so did the hints in the footer.
```
#ONEM SERVICES
A Search
B Information
C Tools
D Business
E Entertainment
F Social
--Reply option/"#"
```

Let's get back to message body. The amount of information displayed to the user, along with header and footer, can exceed the sms size. In this case, the ONEm platform will split body information in several messages called chunks, adding a paging system that allows users to access more than can fit one single SMS. At the end of each sms body, right before the footer, there will be automatically added information about current chunk and total number of chunks in which the message was split. This mechanism applies both to simple text, like a news article, and options lists that are too long to be displayed in one message.
A great example for this mechanism can be extracted from our #wiki application. The article's introduction about SMS is paginated in 8 chunks and the first 2 are presented below. The hint from footer - "more" - is used to navigate to the next chunk.
```
#WIKI (ENGLISH) SMS SEARCH
SMS (short message service) is a text messaging service component of most telephone, Internet, and mobile device systems. It uses standardized
..1/8
--MORE/BACK

>> more

communication protocols to enable mobile devices to exchange short text messages. An intermediary service can facilitate a text-to-voice conversion to be sent to landlines.
SMS was
..2/8
--MORE/BACK
```
Another important topic to talk about regards capturing user input. Any webpage or web application will present users with a form to complete and submit. This is rather difficult in the SMS version of ONEm applications, but getting help from wizards, forms are completed step by step, each form field translates in a new message asking user for a free response or choose from a list of options. When all information is gathered, the user can review and submit the form through a supplementary confirmation step. No worries, we dedicated an entire section to forms and how you can create one [here][
<!-- Link to Building section, Forms  -->
]

To see all these concepts at work, with real ONEm examples, and much more you can watch this Platform Demo
<!-- video here about services and how they work -->


# What are ONEm apps?

The ONEm Framework provides a set of APIs and tools that allow you to rapidly build local or global SMS and web based applications that solve a myriad of business problems.
ONEm Framework is a layer on top of ONEm's cloud-based Platform that provides SMS connectivity to mobile networks around the globe.
Once you register as a developer, based on ONEm principles, you can create your own application and reach the ONEm ecosystem.

The great thing about ONEm Framework is that you can use your favourite programming language and with one codebase, quickly deploy an easy-to-use, dynamic application that is instantly available on SMS and the Web.

# Core concepts

Let's start with the basics.
Follow along the steps to ramp up or watch as we create a working Todo application.
<!-- video here on how to create an app -->

## Developer Account

Head over to the [developer portal](http://developer-portal-poc.onem.zone) and create your account. Once you have an account, go to **Applications** section and create your app.
<!-- tutorial? -->
As a ONEm developer, after you create and register your application on the developer portal you should follow the necessary steps to configure it to return standardised JSON responses upon ONEm requests. These requests are launched by the ONEm platform on behalf of your users.
<!-- Link to Building section, how to register an application  -->

## Your app

Your app is identified by the name you give it and it can be accessed through the ONEm platform by prefixing it with a hashtag.
When your app is being accessed by the user, ONEm platform is performing an **HTTP GET** request to the **callback_url** defined in the developer portal.
This must return a JSON http response and will be used by ONEm platform to compute an sms and send it to the user as a response from your app.
<!-- Link to Building section, how to structure an application  -->

## SDK
<!-- TBD short description and purpose -->
<!-- Link to Building section, SDK  -->

## Framework
<!-- TBD short description and purpose -->
<!-- Link to Building section, Framework  -->

## API
<!-- TBD short description and purpose -->
<!-- Link to API section  -->
