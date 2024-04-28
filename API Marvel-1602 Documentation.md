# API Marvel-1602 Documentation

## **Description**

This API returns the data from the Marvel 1602 comic books. **Marvel 1602** is an eight-issue miniseries from [Marvel Comics](https://pt.wikipedia.org/wiki/Marvel_Comics), written by [Neil Gaiman](https://pt.wikipedia.org/wiki/Neil_Gaiman). The story takes place in the year [1602](https://pt.wikipedia.org/wiki/1602) in the [Marvel Universe](https://pt.wikipedia.org/wiki/Universo_Marvel), where the [superheroes](https://pt.wikipedia.org/wiki/Super-her%C3%B3is) emerged four hundred years earlier.

## **The story**

The main characters must solve the mystery of their own existence, while dealing with intrigues in Queen [Elizabeth's](https://pt.wikipedia.org/wiki/Elizabeth_I_de_Inglaterra) court. All the main characters from the House of Ideas appear in the series. [Nick Fury](https://pt.wikipedia.org/wiki/Nick_Fury) is responsible for British intelligence, [Doctor Strange](https://pt.wikipedia.org/wiki/Doutor_Estranho) is the queen's physician, [Peter Parker](https://pt.wikipedia.org/wiki/Homem-Aranha) (Spider-Man) is Fury's page, the [Daredevil](https://pt.wikipedia.org/wiki/Demolidor) is a blind minstrel who sings about the [Fantastic Four](https://pt.wikipedia.org/wiki/Quarteto_Fant%C3%A1stico), a group of explorers who acquired special powers.

## **Common structures**

| Atributo | Type | Descrição |
| --- | --- | --- |
| _id | String | Unique identifier of the record in the API database. |
| id | Number | The unique identifier for the comic series. |
| title | String | The title of the comic series. |
| description | String | A description of the comic series. |
| startYear | Number | The year of the series' initial release. |
| endYear | Number | The final release year of the series (if applicable). |
| thumbnail | String | Comic book series thumbnail URL. |
| __v | Number | Version of the document in the database. |

## Base URL

The base URL for all API requests is:

`http://localhost:3000/`

# Endpoints

## Characters

### `GET /characters`

Returns a list of all characters from all the comics.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `id`: The unique identifier of the character.
    - `_id`: The unique identifier of the record in the API database.
    - `name`: The name of the character.
    - `description`: A brief description of the character.
    - `thumbnail`: Thumbnail URL of the character.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /characters
```

Response:

```json
[
  {
    "comics": [],
    "_id": "66217f73b7e5033cbc40cb2d",
    "id": 1009281,
    "name": "Doctor Doom",
    "description": "",
    "thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/60/53176bb096d17.jpg",
    "comicsId": [148, 50114, 20630],
    "__v": 0
  },
  {
    "comics": [],
    "_id": "66217f73b7e5033cbc40cb30",
    "id": 1009417,
    "name": "Magneto",
    "description": "",
    "thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/b0/5261a7e53f827.jpg",
    "comicsId": [145, 20630],
    "__v": 0
  },
  ...
 ]
```

### `GET /characters/id/comics`

Returns a list of characters from a specific list.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `id`: The unique identifier of the character.
    - `_id`: The unique identifier of the record in the API database.
    - `name`: The name of the character.
    - `description`: A brief description of the character.
    - `thumbnail`: Thumbnail URL of the character.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /characters/1009417/comics
```

Response:

```json

```

### `GET /characters/id`

Returns data for a specific character.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `_id`: The unique identifier of the record in the API database.
    - `id`: The unique identifier of the character.
    - `name`: The name of the character.
    - `description`: A brief description of the character.
    - `thumbnail`: Thumbnail URL of the character.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /characters/1009281
```

Response:

```json
{
	"comics": [],
	"_id": "66217f73b7e5033cbc40cb2d",
	"id": 1009281,
	"name": "Doctor Doom",
	"description": "",
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/60/53176bb096d17.jpg",
	"comicsId": [
		148,
		50114,
		20630
	],
	"__v": 0
}
```

### `GET /characters/total`

Returns the number of characters.

### Response

Returns a numberobject with the following properties:

- `results`: Returns the number of characters.
    - `Number`: The number of characters.

### Example

Request:

```json
GET /characters/total

```

Response:

```json
9
```

### `POST /characters`

Sends and returns character creation data.

### Parameters

Parameters must be sent in the body in JSON format.

- `id` : The unique identifier.
- `name`: The name of the character.
- `description`: A brief description of the character.
- `thumbnail`: Thumbnail URL of the character.
- `comicsId`: A list of identifiers of the comics in which the character appears.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `_id`: The unique identifier of the record in the API database.
    - `id`: The unique identifier of the character.
    - `name`: The name of the character.
    - `description`: A brief description of the character.
    - `thumbnail`: Thumbnail URL of the character.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```json
POST /characters

{
		"id": 11,
		"name": "name_test",
		"description": "description_test",
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/60/53176bb096d17.jpg",
		"comics": [
			
		]
}
```

Response:

```html
{
	"id": 11,
	"name": "name_test",
	"description": "description_test",
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/60/53176bb096d17.jpg",
	"comics": [],
	"_id": "662c79bcce3e0efec3d9859a",
	"__v": 0
}
```

### `PUT /characters/id`

Update a character's data.

### Parameters

Parameters must be sent in the body in JSON format.

- `name`(optional): The name of the character.
- `description`(optional): A brief description of the character.
- `thumbnail`(optional): Thumbnail URL of the character.
- `comicsId`(optional): A list of identifiers of the comics in which the character appears.

### Response

Returns an HTML status

### Example

Request:

```json
PUT /characters

{
		"name": "test_name_update",
		"description": "test update"
}
```

Response:

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled.png)

### `DELETE /characters/id`

Delete a character by id.

### Parameters

- `id`: The unique identifier of the character.

### Response

Returns an HTML status

### Example

Request:

```json
DELETE /characters/id
```

Response:

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled.png)

## Creators

### `GET /creators`

Returns a list with the creators of the comics.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the creator type, each with the following properties:
    - `id`: The unique identifier of the creator.
    - `_id`: The unique identifier of the record in the API database.
    - `firstName`: The first name of the author
    - `lastName`: The last name of the author.
    - `fullName`: The full name of the author.
    - `thumbnail`: Thumbnail URL of the author.
    - `role`: The role or function of the creator in comics.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /creators
```

Response:

```json
[
	{
		"comics": [],
		"_id": "66217f72b7e5033cbc40cb23",
		"id": 567,
		"firstName": "Neil",
		"lastName": "Gaiman",
		"fullName": "Neil Gaiman",
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg",
		"role": "writer",
		"comicsId": [
			440,
			145,
			146,
			147,
			148,
			377
		],
		"__v": 0
	},
	{
		"comics": [],
		"_id": "66217f72b7e5033cbc40cb26",
		"id": 175,
		"firstName": "Andy",
		"lastName": "Kubert",
		"fullName": "Andy Kubert",
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/f/60/4bc468f4eca4c.jpg",
		"role": "penciller",
		"comicsId": [
			440,
			145,
			146,
			147,
			148,
			377
		],
		"__v": 0
	},
  ...
 ]
```

### `GET /creators/id`

Returns data for a specific creator.

### Parameters

- `id` : The unique identifier.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the creator type, each with the following properties:
    - `id`: The unique identifier of the creator.
    - `_id`: The unique identifier of the record in the API database.
    - `firstName`: The first name of the author
    - `lastName`: The last name of the author.
    - `fullName`: The full name of the author.
    - `thumbnail`: Thumbnail URL of the author.
    - `role`: The role or function of the creator in comics.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /creators/567
```

Response:

```json
{
	"comics": [],
	"_id": "66217f72b7e5033cbc40cb23",
	"id": 567,
	"firstName": "Neil",
	"lastName": "Gaiman",
	"fullName": "Neil Gaiman",
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg",
	"role": "writer",
	"comicsId": [
		440,
		145,
		146,
		147,
		148,
		377
	],
	"__v": 0
}
```

### `GET /creators/id/comics`

Returns data for a specific creator.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the creator type, each with the following properties:
    - `id`: The unique identifier of the creator.
    - `_id`: The unique identifier of the record in the API database.
    - `firstName`: The first name of the author
    - `lastName`: The last name of the author.
    - `fullName`: The full name of the author.
    - `thumbnail`: Thumbnail URL of the character.
    - `role`: The role or function of the creator in comics.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /creators/567/comics
```

Response:

```json

```

### `POST /creators`

Sends and returns creator creation data.

### Parameters

Parameters must be sent in the body in JSON format.

- `id` : The unique identifier.
- `firstName`: The first name of the author
- `lastName`: The last name of the author.
- `fullName`: The full name of the author.
- `thumbnail`: Thumbnail URL of the author.
- `role`: The role or function of the creator in comics.
- `comicsId`: A list of identifiers of the comics in which the character appears.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `id`: The unique identifier of the creator.
    - `_id`: The unique identifier of the record in the API database.
    - `firstName`: The first name of the author
    - `lastName`: The last name of the author.
    - `fullName`: The full name of the author.
    - `thumbnail`: Thumbnail URL of the author.
    - `role`: The role or function of the creator in comics.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```json
POST /creator

{
		"id": 4,
		"firstName": "author_firstName",
		"lastName": "author_lastName",
		"fullName": "author_fullName",
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg",
		"comics": [
	],
	"role": "author_role"
}
```

Response:

```html
{
	"id": 4,
	"firstName": "author_firstName",
	"lastName": "author_lastName",
	"fullName": "Allan Ogawa",
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg",
	"role": "author_role",
	"comics": [],
	"_id": "662c7993ce3e0efec3d98595",
	"__v": 0
}
```

### `PUT /creators/id`

Update a creator data.

### Parameters

Parameters must be sent in the body in JSON format.

- `firstName`(optional): The first name of the author
- `lastName`(optional): The last name of the author.
- `fullName`(optional): The full name of the author.
- `thumbnail`(optional): Thumbnail URL of the author.
- `role`(optional): The role or function of the creator in comics.
- `comicsId`(optional): A list of identifiers of the comics in which the character appears.

### Response

Returns an HTML status

### Example

Request:

```json
PUT /characters
{
		"firstName": "update_test",
		"lastName": "update_test",
		"fullName": "Update test"
}
```

Response:

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled.png)

### `DELETE /creators/id`

Delete a creator by id.

### Parameters

- `id`: The unique identifier of the creator.

### Response

Returns an HTML status

### Example

Request:

```json
DELETE /creators/id
```

Response:

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled.png)

## Comics

### `GET /comics`

Returns a list with the comics.

### Parameters

- `limit` (optional): The maximum number of books to return. Default is 10.
- `offset` (optional): The number of books to skip before starting to return results. Default is 0.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `id`: The unique identifier of the book.
    - `_id`: The unique identifier of the record in the API database.
    - `issueNumber`: The issue number of the comic.
    - `title`: The full title of the comic.
    - `description:` A description of the comic.
    - `onsaleDate`: The release date of the comic.
    - `price`: The price of the comic
    - `thumbnail`: Thumbnail URL of the comic.
    - `__v`: Version of the document in the database.

### Example

Request:

```
GET /comics
```

Response:

```json
[
	{
		"_id": "66217f72b7e5033cbc40cb0a",
		"id": 440,
		"issueNumber": 8,
		"title": "1602 (2003) #8",
		"description": "CLIMATIC last issue! Secrets revealed! Mysteries explained! A mighty sacrifice! Worlds live! Worlds die! Heroes make choices! And so do villains...",
		"onsaleDate": "2004-03-31T05:00:00.000Z",
		"price": 3.99,
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/5/c0/5aa052106f9d3.jpg",
		"__v": 0
	},
	{
		"_id": "66217f72b7e5033cbc40cb0d",
		"id": 145,
		"issueNumber": 7,
		"title": "1602 (2003) #7",
		"description": "Secrets are revealed and coffins are closed as two of our 17th-century Marvel heroes lose their lives in the penultimate chapter to this major, best-selling limited series event!\r\n32 PGS./MARVEL PSR...$3.50",
		"onsaleDate": "2004-02-11T05:00:00.000Z",
		"price": 3.5,
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/c/90/568e6b71aabd8.jpg",
		"__v": 0
	},
  ...
 ]
```

### `GET /comics/total`

Returns the number of comics.

### Example

Request:

```
GET /comics/total
```

Response:

```json
8
```

### `GET /comics/id`

Returns data for a specific comic.

### Parameters

- `id` : The unique identifier.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `id`: The unique identifier of the creator.
    - `_id`: The unique identifier of the record in the API database.
    - `firstName`: The first name of the author
    - `lastName`: The last name of the author.
    - `fullName`: The full name of the author.
    - `thumbnail`: Thumbnail URL of the author.
    - `role`: The role or function of the creator in comics.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```json
GET /comics/id
```

Response:

```json
{
	"_id": "66217f72b7e5033cbc40cb16",
	"id": 148,
	"issueNumber": 4,
	"title": "1602 (2003) #4",
	"description": "With the country in turmoil, Dr. Strange learns Virginia Dare's dark secret, Peter Parquargh is captured by the X-Men, and Fury is placed in an impossible position! 32 PGS./MARVEL PSR...$3.50",
	"onsaleDate": "2003-11-12T05:00:00.000Z",
	"price": 3.5,
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/8/e0/5aa05273b5cd7.jpg",
	"__v": 0
}
```

### `GET /comics/id/characters`

Returns characters by comic id.

### Parameters

- `id` : The unique identifier.

### Response

Returns a list of JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `_id`: The unique identifier of the record in the API database.
    - `id`: The unique identifier of the character.
    - `name`: The name of the character.
    - `description`: A brief description of the character.
    - `thumbnail`: Thumbnail URL of the character.
    - `comicsId`: A list of identifiers of the comics in which the character appears.
    - `__v`: Version of the document in the database.

### Example

Request:

```json
GET /comics/148/characters
```

Response:

```json
[
  {
    "comics": [],
    "_id": "66217f73b7e5033cbc40cb2d",
    "id": 1009281,
    "name": "Doctor Doom",
    "description": "",
    "thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/60/53176bb096d17.jpg",
    "comicsId": [148, 50114, 20630],
    "__v": 0
  },
  {
    "comics": [],
    "_id": "66217f73b7e5033cbc40cb30",
    "id": 1009417,
    "name": "Magneto",
    "description": "",
    "thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/3/b0/5261a7e53f827.jpg",
    "comicsId": [145, 20630],
    "__v": 0
  },
  ...
 ]
```

### `POST /comics`

Sends and returns comic creation data.

### Parameters

Parameters must be sent in the body in JSON format.

- `id`: The unique identifier of the comic.
- `issueNumber`: The issue number of the comic.
- `title`: The full title of the comic.
- `description:` A description of the comic.
- `onsaleDate`: The release date of the comic.
- `price`: The price of the comic
- `thumbnail`: Thumbnail URL of the comic.

### Response

Returns a JSON object with the following properties:

- `results`: An array of objects of the character type, each with the following properties:
    - `results`: An array of objects of the character type, each with the following properties:
        - `_id`: The unique identifier of the record in the API database.
        - `id`: The unique identifier of the character.
        - `name`: The name of the character.
        - `description`: A brief description of the character.
        - `thumbnail`: Thumbnail URL of the character.
        - `comicsId`: A list of identifiers of the comics in which the character appears.
        - `__v`: Version of the document in the database.

### Example

Request:

```json
POST /creator

{
		"id": 111,
		"issueNumber": 9,
		"title": "1602 (2012) #8",
		"description": "CLIMATIC last issue! Secrets revealed! Mysteries explained! A mighty sacrifice! Worlds live! Worlds die! Heroes make choices! And so do villains...",
		"onsaleDate": "2004-03-31T05:00:00.000Z",
		"price": 3.99,
		"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/5/c0/5aa052106f9d3.jpg"
}
```

Response:

```json
{
	"id": 111,
	"issueNumber": 9,
	"title": "1602 (2012) #8",
	"description": "CLIMATIC last issue! Secrets revealed! Mysteries explained! A mighty sacrifice! Worlds live! Worlds die! Heroes make choices! And so do villains...",
	"onsaleDate": "2004-03-31T05:00:00.000Z",
	"price": 3.99,
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/5/c0/5aa052106f9d3.jpg",
	"_id": "662e748223b2fc0769b3b94e",
	"__v": 0
}
```

### `PUT /comics/id`

Update a comic data by id.

### Parameters

Parameters must be sent in the body in JSON format.

- `issueNumber`(optional): The issue number of the comic.
- `title`(optional): The full title of the comic.
- `description`(optional): A description of the comic.
- `onsaleDate`(optional): The release date of the comic.
- `price`(optional): The price of the comic
- `thumbnail`(optional): Thumbnail URL of the comic.

### Response

Returns an HTML status

### Example

Request:

```json
PUT /comics/9
{
		"title": "title_test",
		"price": 13.99
	}
```

Response:

```json
{
	"_id": "662e748223b2fc0769b3b94e",
	"id": 111,
	"issueNumber": 9,
	"title": "999999",
	"description": "CLIMATIC last issue! Secrets revealed! Mysteries explained! A mighty sacrifice! Worlds live! Worlds die! Heroes make choices! And so do villains...",
	"onsaleDate": "2004-03-31T05:00:00.000Z",
	"price": 13.99,
	"thumbnail": "http://i.annihil.us/u/prod/marvel/i/mg/5/c0/5aa052106f9d3.jpg",
	"__v": 0
}
```

### `DELETE /comics/id`

Delete a comic by id.

### Parameters

- `id`: The unique identifier of the comic.

### Response

Returns an HTML status

### Example

Request:

```json
DELETE /comics/id
```

Response:

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled.png)

# Errors

This API uses the following error codes:

- `400 Bad Request`: The request was malformed or missing required parameters.

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled%201.png)

- `401 Unauthorized`: The API key provided was invalid or missing.

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled%202.png)

- `404 Not Found`: The requested resource was not found.

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled%203.png)

- `500 Internal Server Error`: An unexpected error occurred on the server.

![Untitled](API%20Marvel-1602%20Documentation%2066cfc43a55b042629e66ffca0f0d7fd9/Untitled%204.png)