Notes
====================

* [Get notes](#get-notes)
* [Get note](#get-note)
* [Create note](#create-note)
* [Update note](#update-note)
* [Delete note](#delete-note)

Get notes
----------------

* `GET /projects/23423233/notes.json` will return notes added in this project.

```json
[
	{
		"id":451200,
		"title":"Requirements for launch party",
		"description":"",
		"private":false,
		"created_at":"2013-11-05T12:05:53+00:00",
		"updated_at":"2013-11-19T12:22:44+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/notes/451200.json"
	},
	{
		"id":562300,
		"title":"Launch of the New Website",
		"description":"Share ideas on how can we promote this as much possible",
		"private":true,
		"created_at":"2013-10-31T06:31:18+00:00",
		"updated_at":"2013-11-29T07:44:29+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/notes/562300.json"
	}
]
```

Get note
----------------

* `GET /projects/23423233/notes/562300.json` will return the specified note.

```json
{
	"id":"562300",
	"title":"Launch of the New Website",
	"description":"Share ideas on how can we promote this as much possible",
	"content":"A post on our Blog ...",
	"private":true,
	"created_at":"2013-10-31T06:31:18+00:00",
	"updated_at":"2013-11-29T07:44:29+00:00",
	"last_updater":{
		"id":5895623,
		"name":"Stella Altois",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
	},
	"comments":{
		"count":"8",
		"url":"https://api.proofhub.com/v1/projects/23423233/notes/562300/comments.json"
	},
	"collaborators":[
		{
			"id":5895623,
			"name":"Stella Altois"
		}
	]
}
```
Create note
----------------

* `POST /projects/23423233/notes.json` will create a new note from the parameters passed. 
* The collaborators array is an optional list of people IDs that you can get from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). 

```json
{
	"title":"Requirements",
	"description":"Requirements for designing",
	"content":"Mention all that will be required for designing a LOGO for the client.",
	"private":true,
	"collaborators":[5895623, 4634893]
}
```

`201 Created` will be returned along with the JSON of the note ([Get note](#get-note)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update note
----------------

* `PUT /projects/23423233/notes/789456.json` will update the note from the parameters passed.

```json
{
	"title":"Requirements",
	"description":"Requirements for designing the LOGO ",
	"content":"Mention all that will be required for designing a LOGO for the client.",
	"private":false,
}
```

`200 OK` will be returned along with the JSON of the note ([Get note](#get-note)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete note
----------------

* `DELETE /projects/23423233/notes/789456.json` will delete the note.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
