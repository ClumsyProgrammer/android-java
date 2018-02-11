## Βάση Δεδομένων



  Η βάση δεδομένων MySQL έχει εγκατασταθεί τοπικά στον ίδιο host με τον Java server και είναι πλήρως ανεξάρτητη απο αυτόν.
```
Server version      5.5.53-0ubuntu0.14.04.1
Protocol version    10
Connection		    Localhost via UNIX socket
UNIX socket         /var/run/mysqld/mysqld.sock
```

  Εντός της βάσης έχουν δημιουργηθεί αντίστοιχα database και table:

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| CollisionDataBase  | <-- Our database!
| mysql              |
| performance_schema |
+--------------------+
```
```
+-----------------------------+
| Tables_in_CollisionDataBase |
+-----------------------------+
| Record                      |
+-----------------------------+

```

```
mysql> Describe Record;
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| recordID       | varchar(30) | NO   | PRI |         |       |
| terminalID     | varchar(30) | YES  |     | NULL    |       |
| sensorID       | varchar(30) | YES  |     | NULL    |       |
| dangerSTATUS   | varchar(30) | YES  |     | NULL    |       |
| SensorValue    | varchar(30) | YES  |     | NULL    |       |
| EventTimeStamp | varchar(30) | YES  |     | NULL    |       |
| positionX      | varchar(30) | YES  |     | NULL    |       |
| positionY      | varchar(30) | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
```

Από την πλευρά του ο Java Server έχει πρόσβαση στη βάση μέσω ενός jdbc driver με την προσθήκη του αντίστοιχου .jar αρχείου. Όλες οι παράμετροι της σύνδεσης δίνονται ως strings εντός του DataBaseAgent και δεν υπάρχει δυνατότητα αλλαγής μετά τη μεταγλώττιση ή με παρέμβαση του χρήστη.

```
// Connecting to local MySQL DataBase
String DRIVER = "com.mysql.jdbc.Driver";
String DATABASE_URL = "jdbc:mysql://localhost:3306/CollisionDataBase";

// Username and Password
connection = DriverManager.getConnection(DATABASE_URL, "root", "akka");

```