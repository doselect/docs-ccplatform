## Sample MongoDB problem

### Problem name
Add restaurant

### Database
MongoDB

### Type
DDL/DML query based (Evaluation is done using a script)

### Problem Statement
Insert the following document in the `restaurants` collection of `test` database.

```json
{
    "address" : {
        "street" : "2 Avenue",
        "zipcode" : "10075",
        "building" : "1480",
        "coord" : [ -73.9557413, 40.7720266 ]
    },
    "borough" : "Manhattan",
    "cuisine" : "Italian",
    "grades" : [
        {
            "date" : ISODate("2014-10-01T00:00:00Z"),
            "grade" : "A",
            "score" : 11
        },
        {
            "date" : ISODate("2014-01-16T00:00:00Z"),
            "grade" : "B",
            "score" : 17
        }
    ],
    "name" : "Vella",
    "restaurant_id" : "41704621"
}
```

### Solution
```javascript
conn = new Mongo()
db = conn.getDB("test")
db.restaurants.insert(
   {
      "address" : {
         "street" : "2 Avenue",
         "zipcode" : "10075",
         "building" : "1480",
         "coord" : [ -73.9557413, 40.7720266 ]
      },
      "borough" : "Manhattan",
      "cuisine" : "Italian",
      "grades" : [
         {
            "date" : ISODate("2014-10-01T00:00:00Z"),
            "grade" : "A",
            "score" : 11
         },
         {
            "date" : ISODate("2014-01-16T00:00:00Z"),
            "grade" : "B",
            "score" : 17
         }
      ],
      "name" : "Vella",
      "restaurant_id" : "41704621"
   }
)

```

### Testcases

#### Testcase 1
**Positive annotation:** Document is inserted correctly  
**Negative annotation:** Document is not inserted in the required format

```python
# -*- coding: utf-8 -*-
import unittest
from pymongo import MongoClient
import datetime
from bson import ObjectId

expected_document = {
    u'cuisine': u'Italian',
    u'borough': u'Manhattan',
    u'name': u'Vella',
    u'restaurant_id': u'41704621',
    u'grades': [
        {
            u'date': datetime.datetime(2014, 10, 1, 0, 0),
            u'grade': u'A',
            u'score': 11.0
        },
        {
            u'date': datetime.datetime(2014, 1, 16, 0, 0),
            u'grade': u'B',
            u'score': 17.0
        }
    ],
    u'address': {
        u'building': u'1480',
        u'street': u'2 Avenue',
        u'zipcode': u'10075',
        u'coord': [-73.9557413, 40.7720266]
    },
}

class InsertDocumentTest(unittest.TestCase):
        def runTest(self):
                client = MongoClient()
                db = client.test
                restaurants = db.restaurants
                actual_document = restaurants.find_one({"restaurant_id": "41704621"}, {"_id": False})
                self.assertDictEqual(actual_document, expected_document)

if __name__ == "__main__":
        unittest.main()

```
