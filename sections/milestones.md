Milestones
====================

* [Get all milestones](#get-all-milestones)
* [Get milestone](#get-milestone)
* [Create milestone](#create-milestone)
* [Update milestone](#update-milestone)
* [Delete milestone](#delete-milestone)

Get all milestones
----------------

* `GET /projects/23423233/milestones.json` will return milestones for this project.
* `GET /people/4634893/milestones.json` will return milestones assigned to a specified user.


```json
[
	{
		"id":123456,
		"title":"Proccess 1",
		"due_date":"2013-12-02",
		"private":false,
		"completed":true,
		"updated_at":"2013-11-28T10:21:02+00:00",
		"created_at":"2013-11-28T10:21:02+00:00",
		"url":"https://api.proofhub.com/v1/project/23423233/milestones/123456.json"
	},
	{
		"id":963258,
		"title":"Marketing campaign",
		"due_date":"2014-01-20",
		"private":false,
		"completed":false,
		"updated_at":"2013-12-29T16:06:53+00:00",
		"created_at":"2013-12-29T16:06:53+00:00",
		"url":"https://api.proofhub.com/v1/project/23423233/milestones/963258.json"
	}
]
```

Get milestone
----------------

* `GET /project/23423233/milestones/963258.json` will return the specified milestone.

```json
{
	"id":963258,
	"title":"Marketing campaign",
	"due_date":"2014-01-20",
	"private":false,
	"completed":true,
	"updated_at":"2013-12-29T16:06:53+00:00",
	"created_at":"2013-12-29T16:06:53+00:00",
	"creator":{
		"id":4634893,
		"name":"Chris Wagley",
		"image_url":null
	},
	"creator":{
		"id":5895623,
		"name":"Stella Altois",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
	},
	"assigned":[
		{
			"id":4634893,
			"name":"Chris Wagley"
		},
		{
			"id":5895623,
			"name":"Stella Altois"
		}
	]
}
```

Create Milestone
----------------

* `POST /project/23423233/milestones.json` will create a new milestone from the parameters passed. 
* The subscribers array is an optional list of people IDs that you can get from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). 

```json
{
	"title":"Submit sales report",
	"due_date":"2014-01-30",
	"private":true,
	"assigned":[5895623, 4634893] 
}
```

`201 Created` will be returned along with the JSON of the milestone ([Get milestone](#get-milestone)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update milestone
----------------

* `PUT /projects/23423233/milestones/789456.json` will update the milestone from the parameters passed.

```json
{
	"title":"Submit sales report",
	"due_date":"2014-01-25",
	"private":true
}
```

`200 OK` will be returned along with the JSON of the milestone ([Get milestone](#get-milestone)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Complete milestone
----------------

* `PUT /projects/23423233/milestones/789456.json` with the following JSON to complete a milestone. You can pass `false` to incomplete the milestone.

```json
{
	"completed":true
}
```

`200 OK` will be returned along with the JSON of the milestone ([Get milestone](#get-milestone)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete milestone
----------------

* `DELETE /projects/23423233/milestones/789456.json` will delete the milestone.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
