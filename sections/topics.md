Topics
====================

* [Get all topics](#get-all-topics)
* [Get topic](#get-topic)
* [Create topic](#create-topic)
* [Update topic](#update-topic)
* [Delete topic](#delete-topic)

Get all topics
----------------

* `GET /projects/23423233/topics.json` will return topics for this project.

```json
[
	{
		"id":123456,
		"title":"Introduction",
		"description":"Introduction for discussing the marketing process",
		"private":false,
		"attachments":"0",
		"updated_at":"2013-11-30T08:00:50+00:00",
		"created_at":"2013-11-07T07:46:43+00:00",
		"url":"https://api.proofhub.com/v1/project/23423233/topics/123456.json"
	},
	{
		"id":789456,
		"title":"Marketing Strategy",
		"description":"Topic to discuss the marketing strategy for PH",
		"private":true,
		"attachments":"1",
		"updated_at":"2013-11-07T13:08:04+00:00",
		"created_at":"2013-11-07T13:08:04+00:00",
		"url":"https://api.proofhub.com/v1/project/23423233/topics/789456.json"
	}
]
```

Get topic
----------------

* `GET /projects/23423233/topics/789456.json` will return the specified topic.

```json
{
	"id":789456,
	"title":"Marketing Strategy",
	"description":"Topic to discuss the marketing strategy for PH",
	"private":true,
	"updated_at":"2013-11-07T13:08:04+00:00",
	"created_at":"2013-11-07T13:08:04+00:00",
	"comments":{
		"count":"2",
		"url":"https://api.proofhub.com/v1/project/23423233/topics/789456/comments.json"
	},
	"creator":{
		"id":5895623,
		"name":"Stella Altois",
		"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
	},
	"subscribers":[
		{
			"id":5895623,
			"name":"Stella Altois"
		}
	],
	"attachments":[
		{
			"name":"calculation_ph.xlsx",
			"byte_size":"41",
			"created_at":"2013-12-21T07:53:00+00:00",
			"source":"upload",
			"url":"https://docs.google.com/viewer?embedded=true&url=https%3A%2F%2Fsdp_.proofhub.com%2Fview%2Fdoc%2F%3F2176707%2F43981916%2F812b4ba287f5ee0bc9d43bbf5bbe87fb13876123809z%2F5a3304d7f18ed98cc1443a0a02573186%2Fcalculation_sdplabs%5B20120620%5D.xlsx",
			"creator":{
				"id":5895623,
				"name":"Stella Altois",
				"image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
			}
		}
	]
}
```
Create topic
----------------

* `POST /projects/23423233/topics.json` will create a new topic from the parameters passed. The subscribers array is an optional list of people IDs that you want to notify about this topic (see [People API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md#get-people) on how to get the people IDs for a given project).

```json
{
	"title":"New topic for discussion",
	"description":"Topic content...",
	"private":true,
	"subscribers":[
		107754873,
		107754873
	]
}
```

The subscribers array is an optional list of people IDs that you can get the category from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). `201 Created` will be returned along with the JSON of the topic ([Get topic](#get-topic)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

**Attaching files**

Attaching files to a topic requires both the token and the name of the attachment. The token is obtained from the [Create attachments](
https://github.com/sdplabs/proofhub-api/blob/master/sections/attachemnts.md#create-attachment) endpoint, which you must hit first before creating an upload. The name parameter must be a valid filename with an extension. Multiple attachments are allowed.

```json
{
	"title":"New topic for discussion",
	"description":"Topic content...",
	"private":true,
	"attachments":[
		{
		"token":"WSt5b0JZdFZjRjNST1BXblhQRnk5QT09",
		"name":"sample.jpg"
		},
		{
		"token":"UVBEbHZkc2puN3h3VHB2cDlZQ3JWdz09",
		"name":"graphs.png"
		}
	],
	"subscribers":[
		107754873,
		107754873
	]
}
```

Update topic
----------------

* `PUT /projects/23423233/topics/789456.json` will  update the topic from the parameters passed.

```json
{
	"title":"Modify the topic for discussion",
	"description":"Topic content...",
	"private":true,
}

```
`200 OK` will be returned along with the JSON of the topic ([Get topic](#get-topic)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete topic
----------------

* `DELETE /projects/23423233/topics/789456.json` will delete the project.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
