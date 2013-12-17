Assign
===============

Get people assigned to a project
----------------

* `GET /projects/23423233/assigned.json` will return all the people assigned to the project.

```json
[
	{
		"id":4634893,
		"name":"Chris Wagley",
		"email":"chris@email.com",
		"updated_at":null,
		"url":"https://api.proofhub.com/v1/people/.json"
	},
	{
		"id":5895623,
		"name":"Stella Altois",
		"email":"stella@email.com",
		"updated_at":null,
		"url":"https://api.proofhub.com/v1/people/.json"
	}
]
```

Assign people to a project
----------------

* `POST /projects/23423233/assigned.json` will grant access to the project for the ids of people already on the account or new people via email_addresses. 

```json
{
	"ids":[5322423, 6233232, 1056436 ],
	"emails":["michael@email.com", "jade@email.com"]
}
```

To get the ids of people in the account [People](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md).

`200 OK` will be returned if the user is assigned.
