Folders
====================

* [Get folders](#get-folders)
* [Create folder](#create-folder)
* [Update folder](#update-folder)
* [Delete folder](#delete-folder)

Get folders
----------------

* `GET /projects/23423233/folders.json` will return folders for the specified project.

```json
[
	{
		"id":1423456,
		"name":"Phase 1 Documents",
		"created_at":"2013-11-06T07:12:12+00:00"
	},
	{
		"id":"7305681",
		"name":"Analysis Documents",
		"created_at":"2013-10-30 12:12:59"
	}
]
```

Create folder
----------------

* `POST /projects/23423233/folders.json` will create a new folder for the parameter passed.

```json
{
	"title":"Phase II Document"
}
```

`201 Created` will be returned along with the JSON of the folder if the record is added. `403 Forbidden` will be returned in case of invalid access.


Update folder
----------------

* `PUT /projects/23423233/folders/7305681.json` will update the folder for the parameter passed.

```json
{
	"title":"Phase 2 Documents",
}
```

`200 OK` will be returned along with the JSON of the folder if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete folder
----------------

* `DELETE /projects/23423233/folders/7305681.json` will delete the folder specified.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
