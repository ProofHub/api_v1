Categories
====================

* [Get Categories](#get-Categories)
* [Get Category](#get-Category)
* [Create Category](#create-Category)
* [Update Category](#update-Category)
* [Delete Category](#delete-Category)

Get Categories
----------------

* `GET /categories.json` will return all account Categories.

```json
[
	{
		"id":147852,
		"name":"Marketing Projects",
		"default":false,
		"url":"https://api.proofhub.com/v1/categories/147852.json"
	},
	{
		"id":4212015,
		"name":"Default category",
		"default":true,
		"url":"https://api.proofhub.com/v1/categories/4212015.json"
	}
]
```

Get Category
----------------

* `GET /categories/5895623.json` will return the specified Category.

```json
{
	"id":147852,
	"name":"Marketing Projects",
	"default":false,
	"created_at":"2013-10-28T11:40:53+00:00",
}
```

Create Category
----------------

* `POST /categories.json` will create a new Category.

```json
{
	"name":"Rockwall Phase I"
}
```

`201 Created` will be returned along with the JSON of the category ([Get category](#get-category)) if the record is added. 


Update category
----------------

* `PUT /categories/54634432.json` will update the category.

```json
{
	"name":"Rockwall Phase II",
}
```

`200 OK` will be returned along with the JSON of the category ([Get category](#get-category)) if the record is updated. `403 Forbidden` will be returned in case of invalid access.

Delete category
----------------

* `DELETE /categories/54634432.json` will delete the category specified.

`204 No Content` will be returned if the record is deleted. `403 Forbidden` will be returned in case of invalid access.
