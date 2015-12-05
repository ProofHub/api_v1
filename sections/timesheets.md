Timesheets
====================

* [Get timesheets](#get-timesheets)
* [Get timesheet](#get-timesheet)
* [Create timesheet](#create-timesheet)
* [Update timesheet](#update-timesheet)
* [Delete timesheet](#delete-timesheet)

Get timesheets
----------------

* `GET /projects/23423233/timesheets.json` will return timesheets for this project.

```json
[
    {
        "id":9658223,
        "title":"Prepare training material",
        "total_hours":7,
        "private":true,
        "archived":false,
        "estimated_hrs":"10",
        "assigned":"5895623",
        "updated_at":"2013-10-31T08:06:32+00:00",
        "created_at":"2013-10-30T11:42:03+00:00",
        "creator":{
            "id":5895623,
            "name":"Stella Altois",
            "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
        },
        "url":"https://api.proofhub.com/v1/projects/23423233/timesheets\/9658223.json"
    },
    {
        "id":451200,
        "title":"Sample timesheet",
        "total_hours":0,
        "private":false,
        "archived":false,
        "estimated_hrs":0,
        "assigned":"4634893",
        "updated_at":"2013-11-05T12:01:40+00:00",
        "created_at":"2013-11-05T12:01:40+00:00",
        "creator":{
            "id":4634893,
            "name":"Chris Wagley",
            "image_url":null
        },
        "url":"https://api.proofhub.com/v1/projects/23423233/timesheets\/451200.json"
    }
]
```

Get timesheet
----------------

* `GET /projects/23423233/timesheets/9658223.json` will return the specified timesheet along with the time entries made in it.

```json
{
    "id":9658223,
    "title":"Prepare training material",
    "private":true,
    "archived":false,
    "estimated_hrs":"10",
    "assigned":"5895623",
    "updated_at":"2013-10-31T08:06:32+00:00",
    "created_at":"2013-10-30T11:42:03+00:00",
    "creator":{
        "id":5895623,
        "name":"Stella Altois",
        "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
    },
    "time_entries":[
        {
            "id":1254263,
            "description":"Research and analysis",
            "hours":4.5,
            "date":"2013-10-30",
            "task_id":0,
            "updated_at":"2013-10-31T07:11:48+00:00",
            "created_at":"2013-10-31T07:10:47+00:00",
            "creator":{
                "id":5895623,
                "name":"Stella Altois",
                "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
            }
        },
        {
            "id":4524521,
            "description":"Conducted introduction and start off meeting",
            "hours":2.5,
            "date":"2013-10-31",
            "updated_at":null,
            "task_id":0,
            "created_at":"2013-10-31T07:58:05+00:00",
            "creator":{
                "id":5895623,
                "name":"Stella Altois",
                "image_url":"https://assets.proofhub.com/thumb/user/index.php?width=80&height=80&cropratio=1:1&image=123456/812b4ba287f5ee0bc9d43bbf5bbe87fb1370073119.jpg"
            }
        }
    ]
}
```
Create timesheet
----------------

* `POST /projects/23423233/timesheets.json` will create a new timesheet from the parameters passed. 

```json
{
    "title":"Training intern"
    "private":true,
    "estimated_hrs":"60",
    "assigned":[4634893, 5895623]
}
```

`201 Created` will be returned along with the JSON of the timesheet ([Get timesheet](#get-timesheet)) if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update timesheet
----------------

* `PUT /projects/23423233/timesheets/789456.json` will update the timesheet from the parameters passed.

```json
{
	"title":"Training the interns"
}
```

`200 OK` will be returned along with the JSON of the timesheet ([Get timesheet](#get-timesheet)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete timesheet
----------------

* `DELETE /projects/23423233/timesheets/789456.json` will delete the timesheet.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
