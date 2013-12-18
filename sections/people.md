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
		"group":{
			"id":2339532, 
			"name":"RockWall"
		},
		"owner":true,
		"admin":false,
		"image_url":null,
		"profile_color":"#FF5500",
		"created_at":"2013-12-07T06:35:11+00:00",
		"updated_at":"2013-12-10T06:35:11+00:00",
		"url":"https://api.proofhub.com/v1/people/4634893.json"
	},
	{
		"id":5895623,
		"name":"Stella Altois",
		"email":"stella@email.com",
		"group":{
			"id":2339532, 
			"name":"RockWall"
		},
		"owner":false,
		"admin":true,
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
		"profile_color":"#812800",
		"created_at":"2013-11-13T05:15:39+00:00",
		"updated_at":"2013-11-13T05:15:39+00:00",
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
	"group":{
		"id":2339532, 
		"name":"RockWall"
	},
	"owner":false,
	"admin":true,
	"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg",
	"profile_color":"#812800",
	"created_at":"2013-11-13T05:15:39+00:00",
	"updated_at":"2013-11-13T05:15:39+00:00",
	"projects":{
		"count":"5",
		"updated_at":"2013-12-12T13:15:48+00:00",
		"url":"https://api.proofhub.com/v1/people/895623/projects.json"
	},
	"milestones":{
		"count":"1",
		"updated_at":"2013-12-12T13:15:48+00:00",
		"url":"https://api.proofhub.com/v1/people/895623/milestones.json"
	},
	"tasks":{
		"count":"2",
		"updated_at":"2013-12-10T10:33:16+00:00",
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
	"admin":true,
	"group":"15297654",
	"language":"fr"
}
```

Language includes `en`, `fr`. You can get the group from the [groups API](https://github.com/sdplabs/proofhub-api/blob/master/sections/groups.md).

`201 Created` will be returned along with the JSON of the person ([Get person](#get-person)) if the record is added. New people can also be invited directly to the [projects](https://github.com/sdplabs/proofhub-api/blob/master/sections/projects.md#assign-people-to-project).

Update person
----------------

* `PUT /people/5895623.json` will update the person.

```json
{
	"name":"Stella Altois",
	"email":"stella.altois@email.com",
	"admin":true,
	"group":"15297654",
	"language":"en"
}
```

`200 OK` will be returned along with the JSON of the person ([Get person](#get-person)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete person
----------------

* `DELETE /people/5895623.json` will delete the person specified.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
