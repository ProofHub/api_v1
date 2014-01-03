Time
====================

* [Get time](https://github.com/sdplabs/proofhub-api/blob/master/sections/timesheets.md#get-timesheet)
* [Create time](#create-time)
* [Update time](#update-time)
* [Delete time](#delete-time)

Get time
----------------

To get an index of all time entries in a timesheet, see [timesheets](https://github.com/sdplabs/proofhub-api/blob/master/sections/timesheets.md#get-timesheet).

Create time
----------------

* `POST /projects/23423233/timesheets/9658223/time.json` will create a new time entry to the timesheet from the parameters passed. 

```json
{
	"description":"Brainstorm session with potential users",
	"date":"2014-01-01",
	"hours":"1"
}
```

`201 Created` will be returned along with the JSON of the time entry if the record is added. `403 Forbidden` will be returned in case of invalid access.

Update time
----------------

* `PUT /projects/23423233/timesheets/9658223/time/1212123.json` will update the tim entry from the parameters passed.

```json
{
	"description":"Brainstorm session with potential users",
	"date":"2014-01-02",
	"hours":"1.5"
}
```

`200 OK` will be returned along with the JSON of the time entry if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete time
----------------

* `DELETE /projects/23423233/timesheets/9658223/time/1212123.json` will delete the time.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
