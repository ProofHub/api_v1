Comments
====================

* [Get comments](#get-comments)
* [Create comment](#create-comment)
* [Update comment](#update-comment)
* [Delete comment](#delete-comment)

Get comments
----------------

* `GET /projects/23423233/topics/123456/comments.json` will return comments for the specified topic. 

```json
[
	{
		"id":456123,
		"content":"Very informative with plenty of examples of good and not-so-good Web marketing.",
		"updated_at":"2013-11-29T12:13:54+00:00",
		"created_at":"2013-11-29T12:13:54+00:00",
		"creator":{
			"id":4634893,
			"name":"Chris Wagley",
			"image_url":null
		},
		"attachments":null
	},
	{
		"id":229941145,
		"content":"This was a nice discovery session. I got lots of ideas for marketing on the Web.",
		"updated_at":"2013-12-21T10:21:15+00:00",
		"created_at":"2013-12-21T10:21:15+00:00",
		"creator":{
			"id":5895623,
			"name":"Stella Altois",
			"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
		},
		"attachments":[
			{
				"name":"sample.doc",
				"byte_size":13,
				"created_at":"2013-12-21T10:21:14+00:00",
				"source":"upload",
				"url":"https://docs.google.com/viewer?embedded=true&url=https%3A%2F%2Fsdp_.proofhub.com%2Fview%2Fdoc%2F%3F2176707%2F43981916%2F812b4ba287f5ee0bc9d43bbf5bbe87fb13876212745m%2F16a5c52b4f18a1fbf244076189d2c447%2Fsample.doc",
				"creator":{
					"id":5895623,
					"name":"Stella Altois",
					"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
				},
			},
			{
				"name":"sample.pdf",
				"byte_size":326,
				"created_at":"2013-12-21T10:21:14+00:00",
				"source":"upload",
				"url":"https://docs.google.com/viewer?embedded=true&url=https%3A%2F%2Fsdp_.proofhub.com%2Fview%2Fdoc%2F%3F2176707%2F43981916%2F812b4ba287f5ee0bc9d43bbf5bbe87fb1387621274h6%2F5928e0d04f89687c55d9d870805588f0%2Fsample.pdf",
				"creator":{
					"id":5895623,
					"name":"Stella Altois",
					"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
				},
			}
		]
	}
]
```

* `GET /projects/23423233/notes/562300/comments.json` will return comments for the specified note. 

```json
[
	{
		"id":123455,
		"description":"note comment 1",
		"parent":0,
		"created_at":"2013-10-31T06:42:47+00:00",
		"creator":{
			"id":5895623,
			"name":"Stella Altois",
			"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
		}
	},
	{
		"id":451203,
		"description":"sub comment 1",
		"parent":123455,
		"created_at":"2013-10-31T06:44:22+00:00",
		"creator":{
			"id":4634893,
	        "name":"Chris Wagleys",
	        "image_url":null
		}
	}
]
```

* To see all comments for a task, you just GET that task using [Task API](https://github.com/sdplabs/proofhub-api/blob/master/sections/tasks.md#get-task) and they're included and look like this:

```json
[
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
```

Create comment
----------------

* `POST /projects/23423233/<section>/123456/comments.json` will create a new comment from the parameters passed for the commentable described via / -- for example /projects/23423233/topics/123456/comments.json or /projects/23423233/tasks/123456/comments.json. 

```json
{
	"description":"The seminar was very user-friendly. Provided very specific and useful info"
}
```
For adding the comment to the note section `/projects/23423233/notes/562300/comments.json` use the following JSON and you can get the parent comment from the [GET comments](#get-comments) section. If there is no parent comment for the comment being added then set the parent to `0`.

```json
{
	"description":"Here goes the comment...",
	"parent":"9734481"
}
```
 
`201 Created` will be returned along with the JSON of the comment if the record is added. `403 Forbidden` will be returned in case of invalid access.

**Attaching files**

Attaching files to a topic comment requires both the token and the name of the attachment. The token is obtained from the [Create attachments](
https://github.com/sdplabs/proofhub-api/blob/master/sections/attachemnts.md#create-attachment) endpoint, which you must hit first before creating an upload. The name parameter must be a valid filename with an extension. Multiple attachments are allowed. Set folder to `0` if you don't want to upload file in any folder.

```json
{
	"description":"The seminar was very user-friendly. Provided very specific and useful info",
	"attachments":[
		{
			"token":"MnF5aVk3clllbEhUNGo1NllwdCtRUT09",
			"name":"senimar_report.xls",
			"folder":7292113
		}
	]
}
```

Update comment
----------------

* `PUT /projects/23423233/<section>/123456/comments/895623.json` will update the comment from the parameters passed for the section specified ie. topics or tasks. 

```json
{
	"description":"The seminar was very user-friendly, provided very specific and useful info."
}
```

`200 OK` will be returned along with the JSON of the comment if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete comment
----------------

* `DELETE /projects/23423233/<section>/123456/comments/895623.json` will delete the comment for the section specified. 

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
