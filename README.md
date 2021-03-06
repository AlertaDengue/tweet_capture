# Tweet Capture

These notebooks are meant to retrieve tweets related to arboviruses (dengue, zika, chikungunya) from Twitter API. The retrieval is done through streaming (in real time) and the retrieved tweets are stored in a MongoDB collection.

# Main files
* twitter_retriever.ipynb: it captures data from Twitter by streaming method and saves it into a MongoDB collection.  

* data_update_and_analysis.ipynb: updates geolocation data, which are not well organized on source data. It also compares databases if data is collected  from different machines, as data retrieval from twitter might be asyncronous. 

* twitter_geolocation_eda.ipynb: It evaluates the geolocation variables from twitter data, for instance comparing the proportion of each variable from total tweets. 

# About MongoDB
MongoDB is a NoSQL database program which uses JSON-like document (also the data format from twitter API). You might navigate a database by using the browser MongoDB Compass or by using Python library ```pymongo```.

## Installation
* [Manual](https://docs.mongodb.com/manual/installation/)
* For Windows, also install [C Runtime](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows)

## Tutorial
* [Tutorial](https://api.mongodb.com/python/current/tutorial.html)
* [collection level operations](http://api.mongodb.com/python/current/api/pymongo/collection.html)
* [Tools for connecting](https://api.mongodb.com/python/current/api/pymongo/mongo_client.html#pymongo.mongo_client.MongoClient). To connect to cluster: Go to your profile at cloud.mongodb.com >>> click clusters and select your cluster >>> click connect >>> connect your application >>> Find Connection String URI Format

## Dumping and restoring MongoDB Collection:

`mongodump --db DataBaseName --collection collection -o "path/to/folder"`

Copy the generated dump/DataBaseName folder to the new machine. Then, import using mongorestore:

`mongorestore --db DataBaseName /path/to/DataBaseName`
* the dump is the bson unzipped file

Note that /path/to/DataBaseName should be a directory filled with .json and .bson representations of your data.

You can also compress the file on the fly:

`mongodump --db somedb --collection somecollection --out "path/to/folder" --gzip`

# About redundancy
It was suggested by Fiocruz to use some redundancy to capture data. One option might be AWS, which offers services such as Lambda (FaaS) and EC2 (IaaS).
