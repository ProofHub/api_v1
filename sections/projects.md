Projects
====================

* [Get all projects](#get-all-projects)
* [Get project](#get-project)
* [Create project](#create-project)
* [Update project](#update-project)
* [Archive/Activate project](#archiveactivate-project)
* [Delete project](#delete-project)

Get all projects
----------------

* `GET /projects.json` will return all active projects.
* `GET /projects/archived.json` will return all archived projects.

```json
[
	{
		"id":123456,
		"title":"Project 1",
		"description":"Project description goes here",
		"category":{
			"id":147852,
			"name":"Default category"
		},
		"start_date":null,
		"end_date":null,
		"updated_at":"2013-11-13T05:15:39+00:00",
		"archived":false,
		"url":"https://api.proofhub.com/v1/project/123456.json"
	},
	{
		"id":456789,
		"title":"Project 2",
		"description":"Project description goes here",
		"category":{
			"id":852369,
			"name":"Sample category"
		},
		"start_date":"2013-10-28",
		"end_date":"2013-10-31",
		"updated_at":"2013-12-07T06:35:11+00:00",
		"archived":false,
		"url":"https://api.proofhub.com/v1/project/456789.json"
	}
]
```

Get project
----------------

* `GET /projects.json` will return all active projects.

```json
{
	"id":123456,
	"title":"Project 1",
	"description":"Project description goes here",
	"archived":false,
	"category":{
		"id":852369,
		"name":"Sample category"
	},
	"updated_at":"2013-12-07T06:35:11+00:00",
	"creator":{
		"id":895623,
		"name":"Abc Test",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
		"created_at":"2013-12-07T06:35:11+00:00"
	},
	"assigned":{
		"value":"895623,123456"
		"url":"https://api.proofhub.com/v1/projects/assigned?id=123456"
	},
	"files":{
		"count":12,
		"updated_at":"2013-11-19 06:26:04",
		"url":"https://api.proofhub.com/v1/projects/123456/files.json"
	},
	"topics":{
		"count":8,
		"updated_at":"2013-12-07 06:34:47",
		"url":"https://api.proofhub.com/v1/projects/123456/topics.json"
	},
	"task_lists":{
		"count":2,
		"updated_at":"2013-11-08 09:59:26",
		"url":"https://api.proofhub.com/v1/projects/123456/lists.json"
	},
	"milestones":{
		"completed":1,
		"incomplete":3,
		"updated_at":"2013-11-28 10:21:02",
		"url":"https://api.proofhub.com/v1/projects/123456/milestones.json"
	},
	"notes":{
		"count":3,
		"updated_at":"2013-11-08 09:54:22",
		"url":"https://api.proofhub.com/v1/projects/123456/timesheet.json"
	}
}
```
Create project
----------------

* `POST /projects.json` will create a new project from the parameters passed.

```json
{
	"title":"New Project",
	"description":"Parameters to add a new project",
	"start_date":"2013-12-10",
	"end_date":"2013-12-15"
}
```

This will return `201 Created`, with the current JSON representation of the project if the creation was a success. See the **Get project** endpoint for more info. If the account has reached the project limit, you'll see a message `You have reached the project limit` and if the user does not have access to create new projects, you'll see `403 Forbidden`.

Update project
----------------

* `PUT /projects/123456.json` will  update the project from the parameters passed.

```json
{
	"title":"New Project 123",
	"description":"This is a test for updating a project",
	"start_date":"2013-12-10",
	"end_date":"2013-12-15"
}
```

This will return `200 OK` if the update was a success along with the current JSON representation of the project. See the **Get project** endpoint for more info. If the user does not have access to update the project, you'll see `403 Forbidden`.


Archive a project
------------------

* `PUT /projects/123456.json` with the following JSON payload will archive a project (pass `"no"` to activate it again).

```json
{
  	"archived": "yes"
}
```

This will return `200 OK` if the update was a success, along with the current JSON representation of the project. If the user does not have access to update the project, you'll see `403 Forbidden`.

Delete project
----------------

* `DELETE /projects/123456.json` will delete the project specified and return `204 No Content` if that was successful. If the user does not have access to delete the project, you'll see `403 Forbidden`.
