# MongoDB Query

### Dibawah ini merupakan beberapa contoh query MongoDB untuk database academic.

#### 1. Membuat database academic

input:
```
use academic
```
output:
```
switched to db academic
```

#### 2. Menampilkan semua collection dan data dalam database
input:
```
show collections
```
output:
```
department
student
system.indexes
```
#### 3. Membuat atau mengaktifkan database
input:
```
use academic
```
output:
```
switched to db academic
```
#### 4. Membuat collection department
input:
```
db.createCollection('department')
```
output:
```
{ "ok" : 1 }
```
#### 5. Membuat collection student
input :
```
db.createCollection('student')
```
output:
```
{ "ok" : 1 }
```
#### 6. Melihat struktur collection student
input:
```
db.createCollection('student')
```
output:
```
{ "ok" : 1 }
```
#### 7. Menginputkan 5 data ke dalam collection department
input:
```
db.department.insert(
  [
    {code:"IS",name:"Information systems faculty",major:"sistem informasi akuntansi"},
    {code:"ECO",name:"Faculty of Economy",major:"Accounting"},
    {code:"LAW",name:"Faculty of law",major:"Hukum alam"},
    {code:"MED",name:"Faculty of health and medicine",major:"Kedokteran"},
    {code:"ALM",name:"Faculty of alam",major:"sekolah alam"}
  ]
)
```
output:
```
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 5,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
```

#### 8. Menginputkan 3 data ke dalam collection student
input:
```
db.student.insert(
  [
    {studentId:"1501171586",name:"Timothy",address:"kemanggisan 2100",department:
      {
        "$ref" : "department",
        "$id" : ObjectId("58901510ba14805a161fec51"),
        "$db" : "academic"
      }},
      {studentId:"1501171587",name:"Fenetta",address:"Kopo 2100",department:
        {
          "$ref" : "department",
          "$id" : ObjectId("58901510ba14805a161fec54"),
          "$db" : "academic"
        }},
        {studentId:"1501171588",name:"Raditz",address:"Namek 2100",department:
          {
            "$ref" : "department",
            "$id" : ObjectId("58901510ba14805a161fec55"),
            "$db" : "academic"
          }}
  ]
)
```
output:
```
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 3,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
```
#### 9. Melihat isi collection student
input:
```
db.student.find()
```
output:
```
{ "_id" : ObjectId("58901699ba14805a161fec56"), "studentId" : "1501171586", "name" : "Timothy", "address" : "kemanggisan 2100", "department" : DBRef("department", ObjectId("58901510ba14805a161fec51")) }
{ "_id" : ObjectId("58901699ba14805a161fec57"), "studentId" : "1501171587", "name" : "Fenetta", "address" : "Kopo 2100", "department" : DBRef("department", ObjectId("58901510ba14805a161fec54")) }
{ "_id" : ObjectId("58901699ba14805a161fec58"), "studentId" : "1501171588", "name" : "Raditz", "address" : "Namek 2100", "department" : DBRef("department", ObjectId("58901510ba14805a161fec55")) }

```
#### 10. Menampilkan key name dan address dalam collection student
input:
```
db.student.find({},{name:true,address:true})
```
output:
```
{ "_id" : ObjectId("58901699ba14805a161fec56"), "name" : "Timothy", "address" : "kemanggisan 2100" }
{ "_id" : ObjectId("58901699ba14805a161fec57"), "name" : "Fenetta", "address" : "Kopo 2100" }
{ "_id" : ObjectId("58901699ba14805a161fec58"), "name" : "Raditz", "address" : "Namek 2100" }

```
#### 11. Menampilkan key student id,name dan address dalam collection student yang mempunyai studentId tertentu
input:
```
db.student.find({studentId:'1501171586'},{studentId:true,name:true,address:true})
```
output:
```
{ "_id" : ObjectId("58901699ba14805a161fec56"), "studentId" : "1501171586", "name" : "Timothy", "address" : "kemanggisan 2100" }

```
#### 12. Menampilkan semua data student secara berurut berdasarkan name dengan sort() secara ascending maupun descending
input :
```
ascending: db.student.find().sort({name:1})
desscending: db.student.find().sort({name:-1})
```
output:
```
ascending:
{ "_id" : ObjectId("58901699ba14805a161fec57"), "studentId" : "1501171587", "name" : "Fenetta", "address" : "Kopo 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec54")) }
{ "_id" : ObjectId("58901699ba14805a161fec58"), "studentId" : "1501171588", "name" : "Raditz", "address" : "Namek 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec55")) }
{ "_id" : ObjectId("58901699ba14805a161fec56"), "studentId" : "1501171586", "name" : "Timothy", "address" : "kemanggisan 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec51")) }

descending:
{ "_id" : ObjectId("58901699ba14805a161fec56"), "studentId" : "1501171586", "name" : "Timothy", "address" : "kemanggisan 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec51")) }
{ "_id" : ObjectId("58901699ba14805a161fec58"), "studentId" : "1501171588", "name" : "Raditz", "address" : "Namek 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec55")) }
{ "_id" : ObjectId("58901699ba14805a161fec57"), "studentId" : "1501171587", "name" : "Fenetta", "address" : "Kopo 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec54")) }
```

#### 13. Menampilkan semua data department secara berurut berdasarkan name dengan sort() secara ascending maupun descending
input :
```
ascending: db.department.find().sort({name:1})
desscending: db.department.find().sort({name:-1})
```
output:
```
ascending:
{ "_id" : ObjectId("58901510ba14805a161fec52"), "code" : "ECO", "name" : "Faculty of Economy", "major" : "Accounting" }
{ "_id" : ObjectId("58901510ba14805a161fec55"), "code" : "ALM", "name" : "Faculty of alam", "major" : "sekolah alam" }
{ "_id" : ObjectId("58901510ba14805a161fec54"), "code" : "MED", "name" : "Faculty of health and medicine", "major" : "Kedokteran" }
{ "_id" : ObjectId("58901510ba14805a161fec53"), "code" : "LAW", "name" : "Faculty of law", "major" : "Hukum alam" }
{ "_id" : ObjectId("58901510ba14805a161fec51"), "code" : "IS", "name" : "Information systems faculty", "major" : "sistem informasi akuntansi" }


descending:
{ "_id" : ObjectId("58901510ba14805a161fec51"), "code" : "IS", "name" : "Information systems faculty", "major" : "sistem informasi akuntansi" }
{ "_id" : ObjectId("58901510ba14805a161fec53"), "code" : "LAW", "name" : "Faculty of law", "major" : "Hukum alam" }
{ "_id" : ObjectId("58901510ba14805a161fec54"), "code" : "MED", "name" : "Faculty of health and medicine", "major" : "Kedokteran" }
{ "_id" : ObjectId("58901510ba14805a161fec55"), "code" : "ALM", "name" : "Faculty of alam", "major" : "sekolah alam" }
{ "_id" : ObjectId("58901510ba14805a161fec52"), "code" : "ECO", "name" : "Faculty of Economy", "major" : "Accounting" }
```
#### 14. Mencari data student dengan name
input:
```
db.student.find({name:'Timothy'},{})

```
output:
```
{ "_id" : ObjectId("58901699ba14805a161fec56"), "studentId" : "1501171586", "name" : "Timothy", "address" : "kemanggisan 2100", "academic" : DBRef("department", ObjectId("58901510ba14805a161fec51")) }

```
