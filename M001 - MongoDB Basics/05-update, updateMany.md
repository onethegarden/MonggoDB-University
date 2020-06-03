# Update, UpdateMany





**1. UpdateOne()**

- update the first document matching our filter
- first arguments:  specify a filter
- second argument : how we want to update the document

```
db.movieDetails.updateOne({
	title: " The Martian"
},{
	$set:{
		poster:"http://ia.media-imdb.com/images/M/
	}
})
```

 ->  in this case, there is just one movie that is titled the Martain

-> $set operatior update the document matching the filter 







**2. Update operator**

- field 

| name         | Descrription                                                 |
| ------------ | ------------------------------------------------------------ |
| $set         | Sets the value of a field in a document                      |
| $inc         | Increments the value of the field by the specified amount    |
| $currentDate | Sets the value of a field to current date, or Timestamp      |
| $min, max    | only update the field if the specified value is less/greater than the existing field value |





- Array

| name      | Descrription                                                 |
| --------- | ------------------------------------------------------------ |
| $addToSet | Adds elements to an array only if they do not already exist in the set |
| $pop      | Removes the first or last item of an array.                  |
| $pull     | Removes all array elements that match a specified query      |
| $push     | Adds an item to an array                                     |
| $pullAll  | Removes all matching values from an array                    |









**3. updateMany()**

- modify all documents matching the filter 

```
db.movieDetails.updateMany({
	rated: null
},{
	$unset:{
		rated:""
	}
})
```





**4. upserts**

- update + insert
- if this filter doesn't match any documents in collection, will be inserted in the collection

```
db.mocieDetails.updateOne({
	"imdb.id":detail.imdb.id
},{
	$set:detail
},{
	upsert:true
})
```





**5. replaceOne()**

- change only one document, the first found in the server that matches the filter expression, using the $natural  order of documents in the collection





**6. deleteOne(), deleteMany()**