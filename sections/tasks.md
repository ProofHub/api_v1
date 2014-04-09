Tasks
====================

* [Get all tasks](#get-all-tasks)
* [Get task](#get-task)
* [Create task](#create-task)
* [Update task](#update-task)
* [Delete task](#delete-task)

Get all tasks
----------------

* `GET /projects/23423233/todolists/748596/tasks.json` will return task for this todolist.
* `GET /people/4634893/tasks.json` will return task assigned to a specified user.

```json
[
	{
		"id":"784512",
		"title":"Update the template document for the training material.",
		"description":null,
		"due_date":null,
		"parent_id":0,
		"completed":true,
		"position":3,
		"updated_at":"2013-12-28T10:50:47+00:00",
		"created_at":"2013-12-28T10:50:47+00:00",
		"comments":0,
		"attachments":1,
		"url":"https://api.proofhub.com/v1/project/23423233/todolists/748596/tasks/784512.json"
	},
	{
		"id":"124556",
		"title":"Get the completed document reviewed and approved by each and every person responsible.",
		"description":"Get the completed document reviewed and approved in detail.",
		"due_date":null,
		"parent_id":0,
		"completed":true,
		"position":1,
		"updated_at":"2013-12-25T11:05:22+00:00",
		"created_at":"2013-12-25T10:55:35+00:00",
		"comments":1,
		"attachments":3,
		"url":"https://api.proofhub.com/v1/project/23423233/todolists/748596/tasks/124556.json"
	}
]
```

Get task
----------------

* `GET /project/23423233/todolists/748596/tasks/124556.json` will return the specified task.

```json
{
	"id":124556,
	"title":"Get the completed document reviewed and approved by each and every person responsible."
	"description":"Get the completed document reviewed in detail.",
	"start_date":null,
	"due_date":"null",
	"position":1,
	"completed":true,
	"updated_at":"2013-12-25T11:05:22+00:00",
	"created_at":"2013-12-25T10:55:35+00:00",
	"creator":{
        "id":5895623,
        "name":"Stella Altois",
        "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
    },
	"completor":{
		"id":4634893,
        "name":"Chris Wagleys",
        "image_url":null
	},
	"assigned":null,
	"attachments":[
        {
            "name":"calculation_ph.xlsx",
            "byte_size":41,
            "created_at":"2013-12-21T07:53:00+00:00",
            "source":"upload",
            "url":"https://docs.google.com/viewer?embedded=true&url=https%3A%2F%2Fsdp_.proofhub.com%2Fview%2Fdoc%2F%3F2176707%2F43981916%2F812b4ba287f5ee0bc9d43bbf5bbe87fb13876123809z%2F5a3304d7f18ed98cc1443a0a02573186%2Fcalculation_sdplabs%5B20120620%5D.xlsx",
            "creator":{
                "id":5895623,
                "name":"Stella Altois",
                "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
            }
        }
    ],
	"comments":[
		{
	        "id":13995058,
	        "content":"Meeting with the client",
	        "created_at":"2013-12-31T11:05:22+00:00",
	        "creator":{
	            "id":4634893,
	            "name":"Chris Wagley",
	            "image_url":null
	        },
	    },
	    {
	        "id":14008626,
	        "content":"Meeting postponed",
	        "created_at":"2013-12-31T11:30:22+00:00",
	        "creator":{
	            "id":4634893,
	            "name":"Chris Wagley",
	            "image_url":null
	        },
	    }
	]
}
```

Create task
----------------

* `POST /project/23423233/todolists/748596/tasks.json` will create a new task from the parameters passed. 
* The assigned array is an optional list of people IDs that you can get from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). 

```json
{
	"description":"Get it signed",
	"start_date":"2013-12-25",
	"due_date":"2013-12-30",
	"assigned":[4634893, 5895623]
}
```

`201 Created` will be returned along with the JSON of the task ([Get task](#get-task)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

**Attaching files**

Attaching files to a task requires both the token and the name of the attachment. The token is obtained from the [Create attachments](
https://github.com/sdplabs/proofhub-api/blob/master/sections/attachemnts.md#create-attachment) endpoint, which you must hit first before creating an upload. The name parameter must be a valid filename with an extension. Multiple attachments are allowed. Set folder to `0` if you don't want to upload file in any folder.

```json
{
	"description":"Get it signed",
	"start_date":"2013-12-31",
	"due_date":"2013-12-31",
	"attachments":[
		{
			"token":"eUhSL2psVCtWaXU1aG0rOXNCMk1Vdz09",
			"name":"document.doc",
			"folder":0
		}
	],
	"assigned":[4634893, 5895623]
}
```

Update task
----------------

* `PUT /projects/23423233/todolists/789456/tasks/252563.json` will update the task from the parameters passed.

```json
{
	"description":"Get it signed off",
	"start_date":"2013-12-31",
	"due_date":"2013-12-31"
}
```

Complete task
----------------

* `PUT /projects/23423233/todolists/789456/tasks/252563.json` with the following JSON to complete a task. You can pass `false` to incomplete the task.

```json
{
	"completed":true
}
```

`200 OK` will be returned along with the JSON of the task ([Get task](#get-task)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete task
----------------

* `DELETE /projects/23423233/todolists/789456/tasks/252563.json` will delete the task.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
