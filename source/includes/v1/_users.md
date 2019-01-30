#  Users

## Show you a list of all users under a store.

```shell
curl "https://subdomain.mybrightsites.com/api/v1/users?token=GXzAxWkkyYLsESGQTU15"
```

> The above request returns JSON structured like this:

```json
{
  "users": [
    {
      "id": 579,
      "name": "John Doe",
      "username": "johndoe",
      "balance": "12.5",
      "active": true,
      "last_edited_date": "2016-07-01T22:53:03-06:00"
    }
  ],
  "meta": {
    "total": 1,
    "offset": 0,
    "limit": 0
  }
}
```

### HTTP Request

`GET /api/v1/users`

### Query Parameters

Parameter | Description
--------- | -----------
<div><strong>groups </strong></div><div> optional </div> | <div>Filter by groups</div><div> Must be one of: Array, String. </div>
<div><strong>date_created_from </strong></div><div> optional </div> | <div>Filter by date created from</div><div> Invalid date format. Valid format: “YYYY-MM-DD hh:mm:ss” or “YYYY-MM-DD” </div>
<div><strong>date_created_to </strong></div><div> optional </div> | <div>Filter by date created to</div><div> Invalid date format. Valid format: “YYYY-MM-DD hh:mm:ss” or “YYYY-MM-DD” </div>
<div><strong>username </strong></div><div> optional </div> | <div>Filter by username</div><div> Must be a String </div>
<div><strong>active </strong></div><div> optional </div> | <div>Filter by active/inactive users</div><div> Must be one of: true, false, 1, 0 </div>
<div><strong>page </strong></div><div> optional </div> | <div>Pagination page number</div><div> Must be a number. </div>
<div><strong>per_page </strong></div><div> optional </div> | <div>Pagination per page number</div><div> Must be a number. </div>


## Show you the specific information for a user account based on the user ID you supply.

```shell
curl "https://subdomain.mybrightsites.com/api/v1/users/579?token=GXzAxWkkyYLsESGQTU15"
```

> The above request returns JSON structured like this:

```json
{
  "id": 579,
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "active": true,
  "confirmed": true,
  "email": "johndoe@email.com",
  "phone": "+1234567890",
  "company": "BSI",
  "title": "Support Leader",
  "groups": ["Public"],
  "balance": "12.5",
  "orders": [],
  "last_edited_date": "2016-07-01T22:53:03-06:00"
}
```

### HTTP Request

`GET /api/v1/users/:id`

### Query Parameters

Parameter | Description
--------- | -----------
<div><strong>id </strong></div><div> required </div> | <div>User ID</div><div> Must be a number. </div>


## Create a brand new user account in the store.

```shell
curl "https://subdomain.mybrightsites.com/api/v1/users?token=GXzAxWkkyYLsESGQTU15" \
  -X POST \
  -H "Content-Type: application/json" \
  -d @- <<'EOF'
{
  "user": {
    "username": "johndoe",
    "first_name":"John",
    "last_name":"Doe",
    "active":true,
    "email":"johndoe@email.com",
    "phone":"+1234567890",
    "company":"BSI",
    "title":"Support Leader",
    "groups":["Public"],
    "balance":12.5,
    "password":"12345678",
    "cuf_1": "helloworld"
  }
}
EOF
```

> The above request returns JSON structured like this:

```json
{
  "id": 579,
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "active": true,
  "confirmed": true,
  "email": "johndoe@email.com",
  "phone": "+1234567890",
  "company": "BSI",
  "title": "Support Leader",
  "groups": ["Public"],
  "balance": "12.5",
  "orders": [],
  "last_edited_date": "2016-07-01",
  "cuf_1": "helloworld"
}
```

### HTTP Request

`POST /api/v1/users`

### Query Parameters

Parameter | Description
--------- | -----------
<div><strong>user </strong></div><div> required </div> | <div> Must be a Hash </div>
<div><strong>user[username] </strong></div><div> required </div> | <div>Unique username</div><div> Must be a String </div>
<div><strong>user[first_name] </strong></div><div> required </div> | <div>First name</div><div> Must be a String </div>
<div><strong>user[last_name] </strong></div><div> required </div> | <div>Last name</div><div> Must be a String </div>
<div><strong>user[email] </strong></div><div> required </div> | <div>Email</div><div> Must be a String </div>
<div><strong>user[phone] </strong></div><div> optional , nil allowed </div> | <div>Phone number</div><div> Must be a String </div>
<div><strong>user[company] </strong></div><div> optional , nil allowed </div> | <div>Company</div><div> Must be a String </div>
<div><strong>user[title] </strong></div><div> optional , nil allowed </div> | <div>Title</div><div> Must be a String </div>
<div><strong>user[groups] </strong></div><div> optional , nil allowed </div> | <div>Assign groups</div><div> Must be an array of String </div>
<div><strong>user[balance] </strong></div><div> optional , nil allowed </div> | <div>Balance</div><div> Must be a float. </div>
<div><strong>user[note] </strong></div><div> optional , nil allowed </div> | <div>Create comment</div><div> Must be a String </div>
<div><strong>user[password] </strong></div><div> optional , nil allowed </div> | <div>Password</div><div> Must be a String </div>
<div><strong>user[cuf_<custom user field id>] </strong></div><div> optional , nil allowed </div> | <div>Custom User Field</div><div> Must be a String </div>


## Update information for a specific user account based on the user ID you supply.

```shell
curl "https://subdomain.mybrightsites.com/api/v1/users/579?token=GXzAxWkkyYLsESGQTU15" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d @- <<'EOF'
{
  "user": {
    "username": "johndoe",
    "first_name":"John",
    "last_name":"Doe",
    "active":true,
    "email":"johndoe@email.com",
    "phone":"+1234567890",
    "company":"BSI",
    "title":"Support Leader",
    "groups":["Public"],
    "balance":12.5,
    "password":"12345678",
    "cuf_1": "12345678"
  }
}
EOF
```

> The above request returns JSON structured like this:

```json
{
  "id": 579,
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "active": true,
  "confirmed": true,
  "email": "johndoe@email.com",
  "phone": "+1234567890",
  "company": "BSI",
  "title": "Support Leader",
  "groups": ["Public"],
  "balance": "12.5",
  "orders": [],
  "last_edited_date": "2016-07-01",
  "cuf_1": "12345678"
}
```

### HTTP Request

`PUT /api/v1/users/:id`

### Query Parameters

Parameter | Description
--------- | -----------
<div><strong>user </strong></div><div> required </div> | <div> Must be a Hash </div>
<div><strong>user[username] </strong></div><div> optional </div> | <div>Unique username</div><div> Must be a String </div>
<div><strong>user[first_name] </strong></div><div> optional </div> | <div>First name</div><div> Must be a String </div>
<div><strong>user[last_name] </strong></div><div> optional </div> | <div>Last name</div><div> Must be a String </div>
<div><strong>user[email] </strong></div><div> optional </div> | <div>Email</div><div> Must be a String </div>
<div><strong>user[phone] </strong></div><div> optional , nil allowed </div> | <div>Phone number</div><div> Must be a String </div>
<div><strong>user[company] </strong></div><div> optional , nil allowed </div> | <div>Company</div><div> Must be a String </div>
<div><strong>user[title] </strong></div><div> optional , nil allowed </div> | <div>Title</div><div> Must be a String </div>
<div><strong>user[groups] </strong></div><div> optional , nil allowed </div> | <div>Assign groups</div><div> Must be an array of String </div>
<div><strong>user[balance] </strong></div><div> optional , nil allowed </div> | <div>Balance</div><div> Must be a float. </div>
<div><strong>user[increase_balance] </strong></div><div> optional , nil allowed </div> | <div>Increase Balance</div><div> Must be a float. </div>
<div><strong>user[decrease_balance] </strong></div><div> optional , nil allowed </div> | <div>Decrease Balance</div><div> Must be a float. </div>
<div><strong>user[note] </strong></div><div> optional , nil allowed </div> | <div>Create comment</div><div> Must be a String </div>
<div><strong>user[password] </strong></div><div> optional , nil allowed </div> | <div>Password</div><div> Must be a String </div>
<div><strong>user[cuf_<custom user field id>] </strong></div><div> optional , nil allowed </div> | <div>Custom User Field</div><div> Must be a String </div>


## Delete a specific user account based on the user ID you supply.

```shell
curl "https://subdomain.mybrightsites.com/api/v1/users/579?token=GXzAxWkkyYLsESGQTU15" \
  -X DELETE
```

> The above request returns JSON structured like this:

```json
{
  "id": 579,
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "active": true,
  "confirmed": true,
  "email": "johndoe@email.com",
  "phone": "+1234567890",
  "company": "BSI",
  "title": "Support Leader",
  "groups": [],
  "balance": "12.5",
  "orders": [],
  "last_edited_date": "2016-07-01"
}
```

### HTTP Request

`DELETE /api/v1/users/:id`

### Query Parameters

Parameter | Description
--------- | -----------
<div><strong>id </strong></div><div> required </div> | <div>User ID</div><div> Must be a number. </div>

