# [SurrealDB](https://surrealdb.com/)
SurrealDB is open-source __NewSQL__ database suitable for any type of application.
#### Features:
- Data change events
- Permissions
- Schemafull
- Scemaless
- Relaional
- Temporal
- Full-Text search
- Scalable
- Serverless
- Embeded
- Graph
- Realtime
- _Multi-tenant_
- _Acid_

SurrealDB is built with Rust language and was created by [Tobie Morgan Hitchcock](https://www.linkedin.com/in/tobiemorganhitchcock/) and 
[Jaime Morgan Hitchcock](https://www.linkedin.com/in/jaimemorganhitchcock/). It uses its own SQL like language named [SurrealQL](https://surrealdb.com/docs/surrealql). By default it is scemaless 
but can be scemafull. In SurrealDB its really easy to create links between tables and it has event system that trigers when data is changed.

## Instalation
Windows
PowerShell
```shell
iwr https://windows.surrealdb.com -useb | iex
```
[Chocolatey](https://community.chocolatey.org/packages/surreal)
```shell
choco install surreal --pre
```
Linux
```shell
curl -sSf https://install.surrealdb.com | sh
```
MacOS
```shell
brew install surrealdb/tap/surreal
```
Docker
```shell
docker run --rm -p 8000:8000 surrealdb/surrealdb:latest start
```
## Setup
You can use SurrealDB in console or use one [libraries](https://surrealdb.com/docs/integration/libraries).  
I am going to use RestAPI and VSCode [Thunder client](https://www.thunderclient.com/) extention.

#### First of all we need to start our db 
```shell
surreal start --log debug --user root --pass root memory
```
#### Next lets open thunder and add two headers
__NS__ = text - it sets namespace  
__DB__ = text - it sets DB name  

#### Then we need to open Auth tab and set Basic to
__Username__ = root  
__Password__ = root

Setup is done, now we can write our commands in Body tab

#### Usage
Every record in SurrealDB has UniqueID that consists of table name on the right and id on the left of semicolumn. UniqueID can be defined by user: `table:id` or be random: `table:{random}`.
Let's create some humans  
__CREATE:__
```sql
CREATE human:brian SET name="Brian", age=24;
CREATE human:john SET name="John", age=30;
CREATE human:Kevin SET name="Kevin", age=59;
```  
Now let's print all our humans  
__SELECT__
```sql
SELECT * FROM human;
```  
Next we will add skills to all our humans
__UPDATE__
```sql
UPDATE human SET skills += ['breathing', 'walking'];
```  
And let's add best friend to Kevin
```sql
UPDATE human:kevin SET best_friend = human:brian;
```
In SurrealDB we can easily print properties of relations
__SELECT__
```sql
SELECT best_friend.name, best_friend.skills FROM human:kevin;
```  
As well as one-to-one relations SurrealDB supports one-to-many relations
```sql
CREATE job:developer SET salary=5000;
CREATE job:designer SET salary=3500;

UPDATE human:brian SET jobs = ['job:developer', 'job:designer'];
```
Now we can easily get all salaries of kevins best friend
```sql
SELECT best_friend.jobs.salary FROM human:kevin;
```

That were some thing that SurrealDB can do. But there is much more. For example __relations__, __events__, __transactions__ and more.  
Here are some resources:
- [Official DOCS](https://surrealdb.com/docs)
- [Fast video tutorial](https://www.youtube.com/watch?v=LCAIkx1p1k0)
- [_Bigger tutorial_](https://www.youtube.com/watch?v=D41jb4DDIdA)
