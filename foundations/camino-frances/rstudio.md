---
description: The familiar RStudio desktop but on the web.
---

# RStudio

Inside the hospital network, we've deployed instances of RStudio server **per researcher** from GAE13. You can access with an address like:

```
http://uclvlddpragae13:908X
```

`x` will be a number unique to you. You'll also need your RStudio username and password (ask one of the RSE team).

When you start a new session, you should see

```
utilities.R successfully loaded from /workspace/scripts/utilities.R
```

at the end of the console output. It's sourced from your `.Rprofile`.

Simply run the following to connect to the data lake:

```r
con <- connect_to_ducklake()
```

You can then interact with the data using the [DuckDB R package](https://duckdb.org/docs/stable/clients/r). For example

```r
dbExecute(con, "SHOW ALL TABLES;")
first10 <- dbGetQuery(con, "SELECT * FROM camino.bronze.Organisms LIMIT 10")
print(first10),
```

{% hint style="info" %}
## See also

[DuckDB R querying documentation](https://duckdb.org/docs/stable/clients/r#querying)
{% endhint %}
