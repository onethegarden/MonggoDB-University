# Comparison Operator





**1. Comparison**

- For comparison of different BSON type values

> BSON is binary serialization format used to store documents and make remote procedure calls in MongoDB.



| name | Description                                           |
| ---- | ----------------------------------------------------- |
| $eq  | Matches value that are equal to a specified value     |
| $gt  | Matches value that are greater than a specified value |
| $gte | greater than or equal to a specified value            |
| $in  | specified in an array                                 |
| $lt  | less than a specified value                           |
| $lte | less than or equal a specified value                  |
| $ne  | not equal to specified value                          |
| $nin | none of the value specified in array                  |



- example

```
{writers:{$in:["Ethan Coen","Joel Coen"]}}
```









**2. Logical**

- sometimes need to specify the same field more than once in a filter

| name | Description                                                  |
| ---- | ------------------------------------------------------------ |
| $and | Join query clauses with a logical AND returns all documents that match the condition of both clauses |
| $not | Inverts the effect of a query expression and returns documents that do not match the query expression |
| $nor | Joins query clauses with a logical NOR returns all documents that fail to match both clauses |
| $or  | Joins query clauses with a logical OR returns all documents that match the conditions of either clause |



- example

```
db.movieDetails.find({$and:[{"metacritic":{ne:null}},
							{"metacritic":{$exists:true}}]},
							{_id:0, title:1, "metacritic":1})
```

```
{$or:[{"watlev":{$eq:"always dry"}},{"depth":{$eq:0}}]}
```







**3. Element**

| name    | Description                                           |
| ------- | ----------------------------------------------------- |
| $exists | Matches documents that have the specified field       |
| $type   | Selects documents if a field is of the specified type |



- example

```
{"atmosphericPressureChange":{$exists:false}}
```









**4. Array**

| name       | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| $all       | Matches arrays that contain all elements specified in the query |
| $elemMatch | Selects documents if element in the array field matches all the specified |
| $size      | Selects documents if the array field is a specified size     |



```
{"sections":{$all:["AG1","MD1","OA1"]}}

{"sections":{$size:2}}

{"boxOffice":{$elemMatch:{"country":"Germany",
						"revenue":{$gt:17}}}}
						
{"results":{$elemMatch:{$gte:70,$lt:80}}}
```









**6. Evaluation**

| name        | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| $expr       | Allows use of aggregation expressions within the query language |
| $jsonSchema | Validate documents against the given JSON Schema.            |
| $mod        | Performs a modulo operation on the value of a field and selects documents with a specified result |
| $regex      | Selects documents where values match a specified regular expression |

```
{"awards.text":{$regex:/^Won.*/}}
```

