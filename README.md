# MongoDB-and-Mongoose-basic-commands
this repo contains basic commands for CRUD.

___________________________________________________________________________________________________________________________
|
|
| 		 <------------------------ mongoose CRUD commands ------------------------------------------->
|
|				 ********** Create **************
|         
|	  1) model_name.create(data,(err,product)=>{res.send(product)});
|
|				 ********** Find(Read) ************
|
|         1) model_name.find({"query if need perticular"},(err,products)=>{res.send(products)});
|
|         2) model_name.findOne({title:"onkar"},(err,product)=>{res.send(product)});
|
|         3) model_name.findById(id,(err,product)=>{res.json(product)});
|
| 				 **********Update *****************
|         
|         1) model_name.findByIdAndUpdate(id,req.body,{new:true},(err,updated)=>{res.json(updated)})
|
|	  2) model_name.findOneAndUpdate({title:"onkar"},req.body,{new:true},(err,updated)=>{res.json(updated)})
|
|				*********** Delete *****************
|
|	  1) model_name.findByIdAndDelete(id,(err,deleted)=>{res.json(deleted)})
|
|	  2) model_name.findOneAndDelete({title:"onkar"},(err,deleted)=>{res.json(deleted)})
|
|_____________________________________________________________________________________________________________________________

<-----------------------------------basic commands -------------------------------------------->
	db:check database name;
	use dbName:change database or create new;
	show dbs:list of all databases;


<-------------  collections-------------------->
	1)show collections  :- shows list of collections.
	2)db.createCollection("name")  :- creates new collection.
	3)db.createCollection("name",{capped:true, size:1024, max:3})  :-  create new collection of size 1024kb and have max entries upto 3.
	4)db.name.insert({name:"onkar"}) :- used to insert one document.
	5)db.name.insertMany([{name:"onkar"},{name:"onkar"},{name:"onkar"}]) :- used to insert many documents.
	6)db.name.find() :-  shows us all documents inside database.
	7)db.name.renameCollection("newName") :- remanes collection

<---------------------  delet collection and database ------------------------>
	1)db.name.drop() :- this will delete whole collection.
	2)db.dropDatabase() :- this will delete whole database.

<----------------------- update document ---------------------->
	1)db.name.update({name:"xyz"},{$set:{email:"abc@gmail.com"}})  :-here $ set will update only filed given not whole document.
	2)db.user.updateMany( {}, { $rename: { "user": "name" } } )   :- this will update keyname user to name.
	3)db.students.update({ _id: 1 },{ $push: { scores: 89 } })    :-this will push 89 into array "scores".
	4)db.products.update({ sku: "abc123" },{ $inc: { quantity: -2} }) :- this will increment data inside qunatity key by -2
<---------------- remover certain document ------------------>

	1)db.name.remove({email:"abc@gmail.com"})  :- remove certain matching document.
	2)db.name.remove({})  :- remove all documents inside collection.

<-------------- special operations on collections--------------------->

	1)db.name.count()  :- gives total count of documetns in collection
	2)db.name.find().sort({price: 1}) :- sorts documents in Assending order.
	3)db.name.find().sort({price: -1}) :- sorts documents in Decending order.
	4)db.name.find().skip(3) :- returns documents by skipping first 3 documents.
	5)db.name.find().limit(2) :- returns only 2 documents.
	6)db.users.find({$or:[{sports:"cricket"},{sports:"football"}]})  :- this will return objects having sports cricket or football
