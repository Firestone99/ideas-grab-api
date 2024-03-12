# ![Status](https://img.shields.io/badge/status-migrating-red)

<h1 align="center"> ideas-grab-api </h1>

<p align="center">
  <img src="./public/heading1.png" />
</p>

<div align="center">
  
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)

</div>

# API Reference 

## Endpoints
- [Get random idea](#get-random-idea)
- [Get random ideas](#get-random-ideas)
- [Get ideas](#get-ideas)
- [Get search text](#get-search-text)

<br>

## Get random idea

```HTTP
GET /random
```

Returns a single random idea from the database

<br>

**Response**

```js
{
  idea: {
    _id: string,
    idea: string
  }
}
```

<br>

**Example**


```HTTP
GET /random
```

<br>
<br>

## Get random ideas

```HTTP
GET /random-ideas
```

Returns a list of random ideas from the database

<br>

**Query parameters**

| prams 	|  type 	|              description             	| default 	| max 	|
|:-----:	|:-----:	|:------------------------------------:	|:-------:	|:---:	|
| limit 	| `int` 	| number of ideas returned per request 	|    10   	|  25 	|                                                              

<br>

**Response**

```js
{
  count: number,
  ideas: [
    {
      _id: string,
      idea: string
    },...
  ]
}
```

<br>

**Example**


```HTTP
GET /random-ideas
```


```HTTP
GET /random-ideas?limit=15
```

<br>
<br>

## Get ideas

```HTTP
GET /ideas
```

Returns a list of all the ideas from the database (_paginated_)

<br>

**Query parameters**

| prams 	|  type 	|            description            	| default 	| max 	|
|:-----:	|:-----:	|:---------------------------------:	|:-------:	|:---:	|
| limit 	| `int` 	| number of ideas returned per page 	|    10   	|  25 	|
|  page 	| `int` 	| page number                       	|    1    	|     	|

<br>

**Response**

```js
{
  metaData: {
    count: number,
    currentPage: number,
    totalPage: number,
    totalCount: number,
    lastItemIndex: number
  },
  ideas: [
    {
      _id: string,
      idea: string
    },...
  ]
}
```

<br>

**Example**

```HTTP
GET /ideas
```

```HTTP
GET /ideas?page=2&limit=15
```

<br>
<br>

## Get search text

```HTTP
GET /search
```

Returns a list of all the ideas from the database which includes the search text (_paginated_)

<br>

**Query parameters**

|    prams   	|   type   	|                  description                  	| default 	| max 	|
|:----------:	|:--------:	|:---------------------------------------------:	|:-------:	|:---:	|
|    limit   	|   `int`  	|       number of ideas returned per page       	|    10   	|  25 	|
|    page    	|   `int`  	|                  page number                  	|    1    	|     	|
| searchText 	| `string` 	| includes the ideas which contains search text 	| _phone_ 	|     	|
                                                          
<br>

**Response**

```js
{
  metaData: {
    matchedIdeas: number,
    totalCount: number,
    currentPage: number,
    totalPage: number,
    lastItemIndex: number,
    searchText: string
  },
  ideas: [
    {
      _id: string,
      idea: string
    },...
  ]
}
```

<br>

**Example**

```HTTP
GET /search
```

```HTTP
GET /search?searchText=website&page=2&limit=15
```

<br>
<br>
