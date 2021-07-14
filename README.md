# fp-api-design-challenge

Api root `https://api.neightbourhoodcolab.com`

## Basic API info

## API Endpoints

### People

`GET /people/search`

Returns and array of people based on search query parametres.

By default returns all people.

Example endpoint: `GET https://api.neightbourhoodcolab.com/people/search?api_key=my_key&min_age=22&max_occupants=5`

Query options:

| Query         | Description                                                   | Additional info                           |
| ------------- | ------------------------------------------------------------- | ----------------------------------------- |
| api_key       | Api key for authenticating access                             | Required to access API                    |
| limit         | Limits the number of results                                  | Default: 50. If 0, will return all houses |
| min_age       | Query based on minimum age                                    |                                           |
| max_age       | Query based on maximum age                                    |                                           |
| min_occupants | Query based on minimum number of occupants in their household |                                           |
| max_occupants | Query based on maximum number of occupants in their household |                                           |

---

`POST /people`

Add a new person to the database

Example endpoint: `GET https://api.neightbourhoodcolab.com/people?api_key=my_key`

requires body:

- `string name`
- `number numberOfOccupants`
- `number age`

Query options:

| Query   | Description                       | Additional info        |
| ------- | --------------------------------- | ---------------------- |
| api_key | api key for authenticating access | required to access API |

### Houses

Returns all houses and their owners

Example endpoint: `GET https://api.neightbourhoodcolab.com/houses?api_key=my_key`

Query options:

| Query   | Description                       | Additional info                           |
| ------- | --------------------------------- | ----------------------------------------- |
| api_key | api key for authenticating access | required to access API                    |
| limit   | limits the number of results      | default: 50. If 0, will return all houses |

Response

```js
{
	"houses": [
		{
			"owner": {
        "id": number unique id,
        "name": string,
        "age": number,
        "numberOfOccupants": number,
      }
			"house": {
        "id": number unique id,
        "house_number": number,
        "house_name": string,
        "address_line_1":  string,
        "address_line_2":  string or null,
        "address_line_3":  string or null,
        "county": string,
        "postcode": string,
      }
		},
    // ...
	]
}
```

---

`GET /houses/search`

Returns and array of houses based on search query parametres.

By default returns all houses and owners.

Example endpoint: `GET https://api.neightbourhoodcolab.com/houses/search?api_key=my_key&postcode=np255py`

Query options:

| Query        | Description                       | Additional info                           |
| ------------ | --------------------------------- | ----------------------------------------- |
| api_key      | Api key for authenticating access | Required to access API                    |
| limit        | Limits the number of results      | Default: 50. If 0, will return all houses |
| postcode     | Query based on postcode           |                                           |
| house_name   | Query based on house name         |                                           |
| house_number | Query based on house number       |                                           |

## Database

### People Database

- id
- name
- age
- number_of_occupants

### Owners Database

- owner_id
- house_id

### Address Database

- id
- house_number
- house_name
- address_line_1
- address_line_2
- address_line_3
- county
- postcode
