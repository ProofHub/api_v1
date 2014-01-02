Todolists
====================

* [Get all todolists](#get-all-todolists)
* [Get todolist](#get-todolist)
* [Create todolist](#create-todolist)
* [Update todolist](#update-todolist)
* [Delete todolist](#delete-todolist)

Get all todolist
----------------

* `GET /projects/23423233/todolists.json` will return todolists for this project.
* `GET /todolists.json` will return todolists for all active project.

```json
[
	{
		"id":4512352,
		"title":"Training material on technology and its use in IT sector",
		"private":false,
		"list_type":"General List",
		"updated_at":"2013-12-27T05:13:32+01:00",
		"created_at":"2013-12-27T05:13:32+01:00",
		"completed_count":0,
		"remaining_count":8,
		"completed":false,
		"url":"https://api.proofhub.com/v1/project/23423233/todolists/4512352.json"
	},
	{
		"id":748596,
		"title":"Training material on marketing",
		"private":false,
		"list_type":"General List",
		"updated_at":"2013-12-22T06:44:36+01:00",
		"created_at":"2013-12-22T06:44:36+01:00",
		"completed_count":2,
		"remaining_count":0,
		"completed":true,
		"url":"https://api.proofhub.com/v1/project/23423233/todolists/748596.json"
	}
]
```

Get todolist
----------------

* `GET /project/23423233/todolists/748596.json` will return the specified todolist.

```json
{
	"id":160917096,
	"title":"Sample list",
	"private":false,
	"list_type":"General List",
	"updated_at":"2013-12-22T06:44:36+01:00",
	"created_at":"2013-12-22T06:44:36+01:00",
	"completed_count":2,
	"remaining_count":0,
	"completed":true,
	"creator":{
		"id":5895623,
		"name":"Stella Altois",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
	},
	"assigned":[
		{
			"id":5895623,
			"name":"Stella Altois"
		}
	]
}
```

Create todolist
----------------

* `POST /project/23423233/todolist.json` will create a new todolist from the parameters passed. 
* The list type can be `gen` for general list, `bug` for bug list, `chk` for check list and `req` for requirement list.
* The assigned array is an optional list of people IDs that you can get from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). 

```json
{
	"title":"Proposal for campaign",
	"list_type":"gen",
	"private":true,
	"assigned":[4634893, 5895623]
}
```

`201 Created` will be returned along with the JSON of the todolist ([Get todolist](#get-todolist)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update todolist
----------------

* `PUT /projects/23423233/todolist/789456.json` will update the todolist from the parameters passed.

```json
{
	"title":"Proposal for campaign",
	"private":false,
}
```

`200 OK` will be returned along with the JSON of the todolist ([Get todolist](#get-todolist)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete todolist
----------------

* `DELETE /projects/23423233/todolist/789456.json` will delete the todolist.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
