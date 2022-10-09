# ![SurrealDB](https://surrealdb.com/)
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
- _Realtime_
- _Multi-tenant_
- _Acid_
SurrealDB is built with Rust language and was created by ![Tobie Morgan Hitchcock](https://www.linkedin.com/in/tobiemorganhitchcock/) and 
![Jaime Morgan Hitchcock](https://www.linkedin.com/in/jaimemorganhitchcock/). It uses its own SQL like language named SurrealQL. By default it is scemaless 
but can be scemafull. It has data change events.

## Instalation
### Windows
PowerShell
```shell
iwr https://windows.surrealdb.com -useb | iex
```
![Chocolatey](https://community.chocolatey.org/packages/surreal)
```shell
choco install surreal --pre
```
### Linux
```shell
curl -sSf https://install.surrealdb.com | sh
```
### MacOS
```shell
brew install surrealdb/tap/surreal
```
### Docker
```shell
docker run --rm -p 8000:8000 surrealdb/surrealdb:latest start
```
