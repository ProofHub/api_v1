Events
====================

* [Get all events](#get-all-events)
* [Get event](#get-event)
* [Create event](#create-event)
* [Update event](#update-event)
* [Delete event](#delete-event)

Get all events
----------------

* `GET /projects/23423233/events.json` will return events for this project.
* `GET /people/4634893/events.json` will return events assigned to a specified user.


```json
[
	{
		"id":123456,
		"title":"Coming soon",
		"description":"Details will follow",
		"starts_at":"2014-04-23T04:00:00+00:00",
		"ends_at":"2014-04-23T05:00:00+00:00",
		"all_day":false,
		"milestone":false,
		"private":true,
		"updated_at":"2014-04-08T06:01:39+00:00",
		"created_at":"2014-04-08T06:01:39+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/events/123456.json"
	},
	{
		"id":963258,
		"title":"Target completed",
		"description":null,
		"starts_at":"2014-04-18",
		"ends_at":"2014-04-18",
		"all_day":true,
		"milestone":true,
		"private":true,
		"updated_at":"2014-04-11T09:18:26+00:00",
		"created_at":"2014-04-11T09:18:26+00:00",
		"url":"https://api.proofhub.com/v1/projects/23423233/events/963258.json"
	}
]
```

Get event
----------------

* `GET /projects/23423233/events/123456.json` will return the specified event.

```json
{
	"id":123456,
	"title":"Coming soon",
	"description":"Details will follow",
	"starts_at":"2014-04-23T04:00:00+00:00",
	"ends_at":"2014-04-23T05:00:00+00:00",
	"all_day":false,
	"private":true,
	"milestone":false,
	"updated_at":"2014-04-08T06:01:39+00:00",
	"created_at":"2014-04-08T06:01:39+00:00",
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

Create event
----------------

* `POST /projects/23423233/events.json` will create a new event from the parameters passed. 
* The `starts_at` and `ends_at` are either dates if the event is an all day affair or times with timezones if they're not.
* Set the `milestone` to `true` if you want to set any event as a milestone.
* The assigned array is an optional list of people IDs that you can get from the [people API](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md). 
* Proofhub will send a reminder email to all the assigned users if `reminder` is set. `reminder` is the number of minutes before the event is going to occur and this can't be less than 30 mins.

```json
{
	"title":"Milestone type event",
	"description":"Details to follow",
	"starts_at":"2014-04-20",
	"private":true,
	"milestone":true,
	"assigned":[5895623, 4634893]
}
```

```json
{
	"title":"Single-day event",
	"description":"Details to follow",
	"starts_at":"2014-04-20",
	"all_day":true,
	"private":false,	
	"assigned":[5895623, 4634893]
}
```

```json
{
	"title":"Multi-day event",
	"description":"Details to follow",
	"starts_at":"2014-04-20",
	"ends_at":"2014-04-22",
	"private":false,
	"all_day":true,
	"assigned":[5895623, 4634893]
}
```

```json
{
	"title":"Timed event",
	"description":"Details to follow",
	"starts_at":"2014-04-20T15:30:00-05:00",
	"ends_at":"2014-04-20T16:30:00-05:00",
	"private":false,
	"all_day":false,
	"reminder":30,
	"assigned":[5895623, 4634893]
}
```

`201 Created` will be returned along with the JSON of the event ([Get event](#get-event)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update event
----------------

* `PUT /projects/23423233/event/789456.json` will update the event from the parameters passed.

```json
{
	"title":"Timed event",
	"description":"Details to follow",
	"starts_at":"2014-04-20T15:30:00-05:00",
	"ends_at":"2014-04-20T18:30:00-05:00",
	"private":true,
	"all_day":false,
	"assigned":[5895623, 4634893]
}
```

`200 OK` will be returned along with the JSON of the event ([Get event](#get-event)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Complete milestone
----------------

* `PUT /projects/23423233/events/845875.json` with the following JSON to complete a milestone. You can pass `false` to incomplete the milestone.
* Only milestone type events can be completed.

```json
{
	"completed":true
}
```

`200 OK` will be returned along with the JSON of the event ([Get event](#get-event)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete event
----------------

* `DELETE /projects/23423233/milestones/789456.json` will delete the event.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
