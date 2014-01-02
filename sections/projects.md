Projects
====================

* [Get all projects](#get-all-projects)
* [Get project](#get-project)
* [Create project](#create-project)
* [Update project](#update-project)
* [Archive/Activate project](#archiveactivate-project)
* [Delete project](#delete-project)
* [Get people assigned to project](#get-people-assigned-to-project)
* [Assign people to project](#assign-people-to-project)

Get all projects
----------------

* `GET /projects.json` will return all the active projects.
* `GET /projects/archived.json` will return all the archived projects.

```json
[
	{
		"id":23423233,
		"title":"PH Marketing",
		"description":"Project description goes here",
		"category":{
			"id":147852,
			"name":"Marketing Projects"
		},
		"start_date":null,
		"end_date":null,
		"updated_at":"2013-11-13T05:15:39+00:00",
		"archived":false,
		"url":"https://api.proofhub.com/v1/project/123456.json"
	},
	{
		"id":54634432,
		"title":"Rockwall Phase II",
		"description":"Develop and execute the 2014 plan",
		"category":{
			"id":852369,
			"name":"Uncategorized"
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

* `GET /projects.json` will return project specified.

```json
{
	"id":23423233,
	"title":"PH Marketing",
	"description":"Project description goes here",
	"archived":false,
	"category":{
		"id":147852,
		"name":"Marketing Projects"
	},
	"updated_at":"2013-12-07T06:35:11+00:00",
	"creator":{
		"id":5895623,
		"name":"Stella Altois",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
		"created_at":"2013-12-07T06:35:11+00:00"
	},
	"assigned":{
		"value":"4634893,5895623"
		"url":"https://api.proofhub.com/v1/projects/23423233/assigned.json"
	},
	"files":{
		"count":12,
		"updated_at":"2013-11-19T06:26:04+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/files.json"
	},
	"topics":{
		"count":8,
		"updated_at":"2013-12-07T06:34:47+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/topics.json"
	},
	"task_lists":{
		"count":2,
		"updated_at":"2013-11-08T09:59:26+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/lists.json"
	},
	"milestones":{
		"completed":1,
		"incomplete":3,
		"updated_at":"2013-11-28T10:21:02+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/milestones.json"
	},
	"notes":{
		"count":3,
		"updated_at":"2013-11-08T09:54:22+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/timesheet.json"
	}
}
```
Create project
----------------

* `POST /projects.json` will create a new project to the account.

```json
{
	"title":"To the moon",
	"description":"DBX's campaign",
	"category":"147852",
	"start_date":"2013-12-10",
	"end_date":"2013-12-15"
}
```

You can get the category from the [categories API](https://github.com/sdplabs/proofhub-api/blob/master/sections/categories.md).

`201 Created` will be returned along with the JSON of the project ([Get project](#get-project)) if the record is added. `You have reached the project limit` will be returned if the account has reached the project limit. `403 Forbidden` will be returned in case of invalid access.

* To assign people to the project - [Assign people to project](#assign-people-to-project)

Update project
----------------

* `PUT /projects/23423233.json` will update the project from the parameters passed.

```json
{
	"title":"To the moon 2014",
	"description":"DBX's campaign",
	"category":"147852",
	"start_date":"2013-12-10",
	"end_date":"2013-12-15"
}
```
`200 OK` will be returned along with the JSON of the project ([Get project](#get-project)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Archive a project
------------------

* `PUT /projects/23423233.json` with the following JSON to archive a project. You can pass `false` to activate the project.

```json
{
  	"archived": true
}
```

`200 OK` will be returned along with the JSON of the project ([Get project](#get-project)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete project
----------------

* `DELETE /projects/23423233.json` will delete the project.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.


Get people assigned to project
----------------

* `GET /projects/23423233/assigned.json` will return all the people assigned to the project.

```json
[
	{
		"id":4634893,
		"name":"Chris Wagley",
		"email":"chris@email.com",
		"updated_at":null,
		"url":"https://api.proofhub.com/v1/people/5895623.json"
	},
	{
		"id":5895623,
		"name":"Stella Altois",
		"email":"stella@email.com",
		"updated_at":null,
		"url":"https://api.proofhub.com/v1/people/5895623.json"
	}
]
```

Assign people to project
----------------

* `POST /projects/23423233/assigned.json` to assign the existing people with their ids or to new people via their email address. 

```json
{
	"ids":[5322423, 6233232, 1056436],
	"emails":["michael@email.com", "jade@email.com"]
}
```
You can get the ids of existing people on the account from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md#get-people).
