# RStudio Server docker image prepared for connection to SQL Server
Based on official [rocker/geospatial](https://github.com/rocker-org/geospatial) image.

How to connect to SQL Server:

```r
library(RODBC)
db <- odbcDriverConnect("driver=FreeTDS;server=<SERVER NAME OR IP>;port=1433;uid=<USER ID>;pwd=<PASSWORD>;database=<DATABASE NAMWE>;")
query <- " \
  select \
	name = @@servername, \
	version = @@version \
"
df <- sqlQuery(db, query)
View(df)
```

