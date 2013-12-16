People
====================

* [Get people](#get-people)
* [Get person](#get-person)
* [Create person](#create-person)
* [Update person](#update-person)
* [Delete person](#delete-person)

Get people
----------------

* `GET /people.json` will return all people.

```json
[
	{
		"id":4634893,
		"name":"Chris Wagley",
		"email":"chris@email.com",
		"owner":true,
		"admin":false,
		"image_url":null,
		"profile_color":"#FF5500",
		"created_at":2013-12-07T06:35:11+00:00,
		"updated_at":2013-12-10T06:35:11+00:00,
		"url":"https://api.proofhub.com/v1/people/4634893.json"
	},
	{
		"id":5895623,
		"name":"Stella Altois",
		"email":"stella@email.com",
		"owner":false,
		"admin":true,
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
		"profile_color":"#812800",
		"created_at":2013-11-13T05:15:39+00:00,
		"updated_at":2013-11-13T05:15:39+00:00,
		"url":"https://api.proofhub.com/v1/people/5895623.json"
	}
]
```

Get person
----------------

* `GET /people/5895623.json` will return the person.

```json
{
	"id":5895623,
	"name":"Stella Altois",
	"email":"stella@email.com",
	"owner":false,
	"admin":true,
	"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
	"profile_color":"#812800",
	"created_at":2013-11-13T05:15:39+00:00,
	"updated_at":2013-11-13T05:15:39+00:00,
	"projects":{
		"count":"5",
		"updated_at":"2013-12-12 13:15:48",
		"url":"https://api.proofhub.com/v1/people/895623/projects.json"
	},
	"milestones":{
		"count":"1",
		"updated_at":"2013-12-12 13:15:48",
		"url":"https://api.proofhub.com/v1/people/895623/milestones.json"
	},
	"tasks":{
		"count":"2",
		"updated_at":"2013-12-10 10:33:16",
		"url":"https://api.proofhub.com/v1/people/895623/tasks.json"
	}
}
```

Create person
----------------

* `POST /people.json` will add a new person to the account.

```json
{
	"name":"Michael Chase",
	"email":"michael@email.com",
	"admin":"yes"
}
```

`201 Created` will be returned along with the JSON of the person ([Get person](#get-person)) if the record is added. 


Update person
----------------

* `PUT /people/5895623.json` will update the person.

```json
{
	"name":"Stella Altois",
	"email":"stella.altois@email.com",
	"admin":"yes"
}
```

`200 OK` will be returned along with the JSON of the person ([Get person](#get-person)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete person
----------------

* `DELETE /people/5895623.json` will delete the person specified.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
