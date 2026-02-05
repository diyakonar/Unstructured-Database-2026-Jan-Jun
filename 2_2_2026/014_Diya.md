# MongoDB Compass – Using CLI (mongosh)

## Question
**Use MongoDB Compass CLI to add students:**
1. Insert **1 student** using `insertOne`
2. Insert **4 students** using `insertMany`

---

## Requirements
- MongoDB installed
- MongoDB Compass installed
- Access to **MongoDB Shell (mongosh)** via Compass

---

## Steps to Follow

### 1. Open MongoDB Compass
- Launch **MongoDB Compass**
- Connect to your MongoDB server (usually `mongodb://localhost:27017`)

---

### 2. Open MongoDB Shell (CLI)
- In MongoDB Compass, click on **`>_ Open MongoDB Shell`**
- This opens **mongosh (CLI)** inside Compass

---

### 3. Create / Switch Database
use college

### 4. Insert 1 Student using insertOne
db.students.insertOne({
  rollNo: 1,
  name: "Student One",
  age: 20,
  department: "CSE"
})

### 5. Insert 4 Students using insertMany
db.students.insertMany([
<br>
  {
    rollNo: 2,
    name: "Student Two",
    age: 21,
    department: "ECE"
  },
  <br>
  {
    rollNo: 3,
    name: "Student Three",
    age: 22,
    department: "IT"
  },
  <br>
  {
    rollNo: 4,
    name: "Student Four",
    age: 20,
    department: "ME"
  },
  <br>
  {
    rollNo: 5,
    name: "Student Five",
    age: 23,
    department: "CE"
  }
  <br>
])

### 6.Remove the 1st record
db.students.deleteOne({ rollNo: 1 })

## output:
{
  acknowledged: true,
  deletedCount: 1
}

### 7.Query all students in Computer department
db.students.find({ department: "computer" }).pretty()

## output:
{
  "_id" : ObjectId("65c1a1a1a1a1"),
  "rollNo" : 2,
  "name" : "Student Two",
  "age" : 21,
  "department" : "computer"
}
<br>
{
  "_id" : ObjectId("65c1a1a1a1a2"),
  "rollNo" : 3,
  "name" : "Student Three",
  "age" : 22,
  "department" : "computer"
}


### 8.Update "computer" department to "bca"
db.students.updateMany(
  { department: "computer" },
  { $set: { department: "bca" } }
)

## output:
{
  acknowledged: true,
  matchedCount: 2,
  modifiedCount: 2
}

### Verify the Update
db.students.find().pretty()

## output:
{
  "_id" : ObjectId("65c1a1a1a1a1"),
  "rollNo" : 2,
  "name" : "Student Two",
  "age" : 21,
  "department" : "bca"
}
<br>
{
  "_id" : ObjectId("65c1a1a1a1a2"),
  "rollNo" : 3,
  "name" : "Student Three",
  "age" : 22,
  "department" : "bca"
}
<br>
{
  "_id" : ObjectId("65c1a1a1a1a3"),
  "rollNo" : 4,
  "name" : "Student Four",
  "age" : 20,
  "department" : "ME"
}
<br>
{
  "_id" : ObjectId("65c1a1a1a1a4"),
  "rollNo" : 5,
  "name" : "Student Five",
  "age" : 23,
  "department" : "CE"
}
