# Insert, InsertMany





**Creating Documents : insertOne()**

1. Using Compass 

![screenshot](./image/02-3.JPG)

2.  Using MongoShell

```
db.movies.insertOne({title:"Star Trek II: The Wrath of Khan", year:1982, imdb:"tt0084726"})
```



if I successed 



```
{
        "acknowledged" : true,
        "insertedId" : ObjectId("5ecbc9366ebbaab8e85e4825")
}
```





> objectID ? 
>
> - MongoDB create the underscore ID value for us
> - Unique identifier for a given document within a collection
> - Contains a 12 byte description that matches this specification.









**Ddb.collection.InsertMany**

```
db.collection.insertMany(
   [ <document 1> , <document 2>, ... ],
   {
      writeConcern: <document>,
      ordered: <boolean>
   }
)
```

1. document :  An array of documents collection
2. writeConcern : A document expressing the write concern
3. ordered : A Boolean specifying whether the mongod instance sholud perform an ordered or unordered insert. Default True











examples : 

```
db.myMovies.insertMany(
  [
    {
      "_id" : "tt0084726",
      "title" : "Star Trek II: The Wrath of Khan",
      "year" : 1982,
      "type" : "movie"
    },
    {
      "_id" : "tt0796366",
      "title" : "Star Trek",
      "year" : 2009,
      "type" : "movie"
    },
    {
      "_id" : "tt0084726",
      "title" : "Star Trek II: The Wrath of Khan",
      "year" : 1982,
      "type" : "movie"
    },
    {
      "_id" : "tt1408101",
      "title" : "Star Trek Into Darkness",
      "year" : 2013,
      "type" : "movie"
    },
    {
      "_id" : "tt0117731",
      "title" : "Star Trek: First Contact",
      "year" : 1996,
      "type" : "movie"
    }
  ],
  {
    ordered: false
  }
);
```



**insertMany() transactions**

- multi-document transactions 