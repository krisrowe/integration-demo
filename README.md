# Environment Preparation

## Database
## Client setup
First get the Cloud SQL Auth proxy as described at https://cloud.google.com/sql/docs/mysql/sql-proxy#install
### Example
```
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy
```
Install the mysql client
```
apt-get install default-mysql-client 
```
## Server setup
Now open two shell windows...

### Shell Window 1
```
./cloud_sql_proxy -instances=bap-amer-south-demo1:us-central2:integration-demo=tcp:3306
```

### Shell Window 2
```
DB_PWD=$(gcloud secrets versions access latest --secret=integration-demo-products-db-pwd)
mysql -u root -p --password=$DB_PWD --host 127.0.0.1 --port 3306
```

# Demo
## Prep 
### Client setup
First get the Cloud SQL Auth proxy as described at https://cloud.google.com/sql/docs/mysql/sql-proxy#install
#### Example
```
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy
```
Install the mysql client
```
apt-get install default-mysql-client 
```

## Show data source
```
use catalog;
select * from products;
```


