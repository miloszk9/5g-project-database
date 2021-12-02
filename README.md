# 5g-project-database

## On test database
```
docker-compose up -d --build

docker build . -t liquibase/liquibase-mysql

docker run --rm --network 5g-project-database_default liquibase/liquibase-mysql --url="jdbc:mysql://mysql_db:3306/test_db" --changeLogFile=dbchangelog.xml --username=root --password=root update
```

## On remote database
```
docker build . -t liquibase/liquibase-mysql

docker run --rm liquibase/liquibase-mysql --url="jdbc:mysql://<DB_ID>:3306/<DB_NAME>" --changeLogFile=dbchangelog.xml --username=<DB_USER> --password=<DB_PASSWORD> update
```

## Get current db config
local:
```
docker run --rm --network 5g-project-database_default liquibase/liquibase-mysql --url="jdbc:mysql://mysql_db:3306/test_db" --changeLogFile=dbchangelog.xml --username=root --password=root generateChangeLog; cat dbchangelog.xml
```