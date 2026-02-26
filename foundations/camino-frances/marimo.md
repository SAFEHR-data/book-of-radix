---
description: A modern Python notebook environment.
---

# marimo

Inside the hospital network we've deployed instances of marimo **per researcher** from GAE13. You can access with an address like:

```
http://uclvlddpragae13:908X
```

`x` will be a number unique to you. You'll also need your marimo password (ask one of the RSE team).



To connect to the database for the first time, run the following in a new notebook:

```python
import duckdb
con = duckdb.connect('/hub/Camino_Bronze.db', read_only=True)
```

You'll need to specify `read_only=True` . (Unfortunately, the default is `read_only=False`, but you don't have write access to theCamino data, so you'll get an error.)

Once you've connected, you can [interact via SQL](https://docs.marimo.io/guides/working_with_data/sql/#example) (choose SQL cells) or in Python using the [DuckDB Python library](https://duckdb.org/docs/stable/clients/python/overview), or with the [visual database explorer on the sidebar](https://docs.marimo.io/guides/editor_features/panels/) of the interface. (Or a mix of all three.)

{% hint style="info" %}
## See also

* [marimo user documentation](https://docs.marimo.io/guides/)
* [DuckDB Python library documentation](https://duckdb.org/docs/stable/clients/python/overview)
{% endhint %}
