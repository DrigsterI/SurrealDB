#### CREATE
```sql
CREATE human:brian SET name="Brian", age=24;
CREATE human:john SET name="John", age=30;
CREATE human:kevin SET name="Kevin", age=59;
```
#### READ
```sql
SELECT * FROM human;
SELECT age FROM human;
SELECT name FROM human:brian;
```
#### UPDATE
```sql
UPDATE human SET skills += ['breathing', 'walking'];
```
#### CREATE RELATIONS
```sql
UPDATE human:kevin SET best_friend = human:brian;
```
#### READ RELATIONS
```sql
SELECT best_friend.name, best_friend.skills FROM human:kevin;
```
#### CREATE MULTIPLE RELATIONS
```sql
CREATE job:developer SET salary=5000;
CREATE job:designer SET salary=3500;
UPDATE human:brian SET jobs = ['job:developer', 'job:designer'];
```
#### DEEP READ RELATIONS
```sql
SELECT best_friend.jobs.salary FROM human:kevin;
```
#### TRANSACTIONS
```sql
CREATE account:one SET balance = 1356;
CREATE account:two SET balance = 156;
```
```sql
BEGIN TRANSACTION;
UPDATE account:one SET balance -= 300.00;
UPDATE account:two SET balance += 300.00;
COMMIT TRANSACTION;
```
```sql
BEGIN TRANSACTION;
UPDATE account:one SET balance += 1000000;
UPDATE account:two SET balance -= 1000000;
CANCEL TRANSACTION;
```
