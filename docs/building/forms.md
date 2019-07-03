A form is like a collection of menus or raw responses and it is basically collecting information from the user.

It is composed by a **header**, a **body** and a **footer**. The body represents form items and these can be slightly modified menus or raw responses.

The form items are being processed in a successive manner. After all the form items have been processed, the user can confirm his choices or reset any of them.

## Json Structure

Your server must return a JSON response with a structure similar to the one below:

```
{'body': [{'type': 'string',
           'name': 'descr',
           'description': 'Provide a description',
           'method': 'POST',
           'path': '/callback-path'},
          {'type': 'date'
           'name': 'due_date',
           'header': 'due date',
           'description': 'Provide a due date'},
          {'type': 'menu',
           'name': 'prio',
           'header': 'priority',
           'body': [{'type': 'option',
                     'value': 'high',
                     'description': 'High priority'},
                    {'type': 'option',
                     'value': 'low',
                     'description': 'Low priority'}]],
 'header': 'create task',
 'footer': None,
 'meta': {'confirmation_needed': False},
 'method': 'POST',
 'path': '/task/create',
 'type': 'form'}
```

Notice the **'type': 'form'** key value pair, which indicates the form response.

So when the user sends **a** to access the **New todo** option item, as mentioned [here](/building/menus/) ONEm will send a GET request to **http://your-callback.url/task/create/**. This url should return something like the above json structure.

The user will be taken through a wizard and it will look like:

```
#TODO CREATE TASK
Provide a description
```

This is the first step and whatever the user replies with will be set as the task description. This is a **string** and it will be **POST**ed to **path** as indicated in the json structure. Notice there is no **header** or **footer** mentioned at this step, so form header and footer will be used as fallbacks.


```
#TODO DUE DATE
Provide a description
```

This is the second step and the user needs to reply with a date. There is no callback path so no HTTP request will be performed after this step. The **header** is present here, so it will be displayed instead of the form header.


```
#TODO PRIORITY
A High priority
B Low priority
--Reply A-B
```

This is the last step and the user needs to choose one option.

After all steps have been processed, as indicated through **method** and **path**, an HTTP POST will be sent to the path which is relative to the callback url: **http://your-callback.url/task/create/** under the mapping **form_item_name=user_choice**

So the POST will look like: **?name=some_description&date=2019-10-10&prio=high**


## Type
The response **type** should be equal to **form** to indicate a form response.

## Meta
The **meta** key holds a dictionary which can contain one of the following keys:

- **confirmation_needed** - if set to false, there won't be any confirmation screen at the end of the form (defaults to true)
- **completion_status_show** - if set to true, there will be a completion status shown (defaults to false)
- **completion_status_in_header** - if set to true, the status will be shown in the header (defaults to false, applicable only when status is shown)

## Header
The header of the form is indicated through **header** key. This value is not final and will be altered by the ONEm platform, by making it uppercased and placing the name of your app in front of it.


## Footer
The footer of the form is indicated through **footer** key and like the header of the form, it is not final and will be altered by the ONEm platform. If no footer is specified, a default might be set.

## Body
The body holds a sequence of dictionaries. Each dictoinary is called a form item and it is described through the below keys:

- **type** - the form item type: _string, int, float, date, datetime, menu_
- **name** - the form item name - this is an identifier and it is used in the information collection process
- **description** - the form item description
- **path** - if exists, an HTTP request will be made after the user submitted his choice
- **method** - indicates how the HTTP request will be made (GET, POST, etc...)
- **header** - indicates the header for this form item and will overwrite the form **header**
- **footer** - indicates the footer for this form item and will overwrite the form **footer**

## Form Item Menu

Aside from the above mentioned form items (strings, integers, etc), a form body can contain a form item menu. Think of it as the select tag in the HTML world. Structure wise, this is a [menu](/building/menus/) slightly modified:

- there is a **name** indicating the form item name
- the **body** contains menu items without any **path** for option items, just **value** which will be set as choice upon user selection
