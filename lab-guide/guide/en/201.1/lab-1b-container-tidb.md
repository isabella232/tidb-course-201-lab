# Lab 201.1.1b: Launch TiDB Database in a Container as a Lab Environment on MacOS/Windows/Linux

## Objective
In an environment that supports Docker Desktop, run TiDB container image and expose the SQL interface of TiDB.

## Prerequisites
+ Internet connection.
+ Operating System already supports container, for example: Docker Desktop is installed for [MacOS or Windows](https://www.docker.com/products/docker-desktop), or [Linux Docker Engine](https://hub.docker.com/search?offering=community&operating_system=linux&q=&type=edition)
+ Database client installed:
  + Recommand: [MySQL client](https://google.com/search?q=MacOS+mysql+client+install)
  + Alternative: [MySQL Workbench (be noted, the version should be: 6.3.10, landing page might show the latest version instead)](https://downloads.mysql.com/archives/workbench/)

## Steps

------------------------------------------------------
#### 1. Launch a sandbox database
+ Open the Terminal (Windows is `CMD` ), the prompt apears, for example: `$ ` or `% ` (Windows is `C:\> `)
+ Start container with `pingcap/tidb` image:
  ```
  $ docker run --name classroom -p 127.0.0.1:4000:4000 pingcap/tidb:latest
  ```

------------------------------------------------------
#### 2. Open another terminal, execute the following command to access the TiDB database using the database client, and the `"mysql> "`prompt appears:
```
$ mysql -h 127.0.0.1 -P 4000 -uroot
```

------------------------------------------------------
#### 3. Check database version:
```sql
select version();
```

------------------------------------------------------
#### 4. Exit the database session (if needed)
```sql
exit
```

------------------------------------------------------
#### 5. Stop the test database:
```
$ docker stop classroom
```

------------------------------------------------------
#### 6. Start the database again:
```
$ docker start classroom
```

------------------------------------------------------
### Output Samples

------------------------------------------------------
#### Reference output for Step 1:
```
$ docker run -p 127.0.0.1:4000:4000 pingcap/tidb:latest
[2022/01/25 09:38:19.811 +00:00] [INFO] [printer.go:34] ["Welcome to TiDB."] ["Release Version"=v6.0.0] [Edition=Community]
[2022/01/25 09:38:19.812 +00:00] [INFO] [trackerRecorder.go:29] ["Mem Profile Tracker started"]
.
.
.
[2022/01/25 09:38:20.004 +00:00] [INFO] [server.go:247] ["server is running MySQL protocol"] [addr=0.0.0.0:4000]
[2022/01/25 09:38:20.004 +00:00] [INFO] [server.go:263] ["server is running MySQL protocol"] [socket=/tmp/tidb-4000.sock]
[2022/01/25 09:38:20.004 +00:00] [INFO] [http_status.go:87] ["for status and metrics report"] ["listening on addr"=0.0.0.0:10080]
[2022/01/25 09:38:20.005 +00:00] [INFO] [domain.go:1301] ["init stats info time"] ["take time"=2.078047ms]
[2022/01/25 09:38:20.005 +00:00] [INFO] [profile.go:92] ["cpu profiler started"]
```
