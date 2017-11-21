## Sample SQL problem

### Problem name
Create table 1

### Database
MySQL

### Problem Statement
- Create a database named `organization`
- In the database `organization`, create the following table

Table name: `Employee`

#### Fields
```
EmployeeId : INT (Primary key)
LastName : NVARCHAR(20) (do not accept NULL value)
FirstName : NVARCHAR(20) (do not accept NULL value)
Title : NVARCHAR(30)
BirthDate : DATETIME
JoiningDate : DATETIME
Address : NVARCHAR(70)
City : NVARCHAR(40)
State : NVARCHAR(40)
Country : NVARCHAR(40)
PostalCode : NVARCHAR(10)
Phone : NVARCHAR(24)
Email : NVARCHAR(60)
```
- Insert a record with the following values
```
EmployeeId : 40211
LastName : Bar
FirstName : Foo
Title : Engineer
BirthDate : 1992-05-10
JoiningDate : 2017-11-21
Address : XYZ
City : Bengaluru
State : Karnataka
Country : India
PostalCode : 560008
Phone : 9999999999
Email : xyz@xyz.com
```

### Solution
```sql
CREATE DATABASE organization;
USE organization;
CREATE TABLE Employee (
    EmployeeId INT NOT NULL,
    LastName NVARCHAR(20) NOT NULL,
    FirstName NVARCHAR(20) NOT NULL,
    Title NVARCHAR(30),
    BirthDate DATETIME,
    JoiningDate DATETIME,
    Address NVARCHAR(70),
    City NVARCHAR(40),
    State NVARCHAR(40),
    Country NVARCHAR(40),
    PostalCode NVARCHAR(10),
    Phone NVARCHAR(24),
    Email NVARCHAR(60),
    CONSTRAINT PRIMARY KEY (EmployeeId));

INSERT INTO Employee VALUES (40211, 'Bar', 'Foo', 'Engineer', '1992-05-10', '2017-11-21', 'XYZ', 'Bengaluru', 'Karnataka', 'India', '560008', '9999999999', 'xyz@xyz.com');
```

### Testcases

#### Testcase 1
**Positive annotation:** Primary key has been set correctly  
**Negative annotation:** Primary key has not been set correctly

```python
import _mysql

db = _mysql.connect()

try:
    db.query("USE organization")
    db.query("show index from Employee where Key_name='PRIMARY'")
    r = db.store_result()
    primary_key = r.fetch_row()[0][4]
    assert(primary_key == "EmployeeId")
    
    
except Exception as e:
    print(e)
    exit(1)

```

#### Testcase 2
**Positive annotation:** Data inserted in the required format in the table  
**Negative annotation:** Data is not inserted in the required format

```python
import _mysql

db = _mysql.connect()

try:
    db.query("USE organization")
    db.query("""SELECT
EmployeeId, LastName, FirstName, Title, BirthDate, JoiningDate, Address, City, State, Country, PostalCode, Phone, Email
FROM Employee
WHERE EmployeeId = 40211
""")
    r = db.store_result()
    result = r.fetch_row()[0]
    assert(result[0] == "40211")
    assert(result[1] == "Bar")
    assert(result[2] == "Foo")
    assert(result[3] == "Engineer")
    assert(result[4] == "1992-05-10 00:00:00")
    assert(result[5] == "2017-11-21 00:00:00")
    assert(result[6] == "XYZ")
    assert(result[7] == "Bengaluru")
    assert(result[8] == "Karnataka")
    assert(result[9] == "India")
    assert(result[10] == "560008")
    assert(result[11] == "9999999999")
    assert(result[12] == "xyz@xyz.com")
    
except Exception as e:
    print(e)
    exit(1)

```
#### Testcase 3
**Positive annotation:** EmployeeId, LastName, FirstName do not allow NULL values  
**Negative annotation:** NULL values are allowed in EmployeeId, LastName or FirstName

```python
import _mysql

db = _mysql.connect()

try:
    db.query("USE organization")
    try:
        db.query("Insert into Employee(Email) VALUES('xyz@xyz.com')")
        exit(1)
    except:
        pass
    
except Exception as e:
    print(e)
    exit(1)

```
