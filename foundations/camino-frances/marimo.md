---
description: A modern Python notebook environment.
---

# marimo

Inside the hospital network, we've deployed instances of marimo **per researcher** from GAE13. You can access with an address like:

```
http://uclvlddpragae13:908X
```

`x` will be a number unique to you. You'll also need your marimo password (ask one of the RSE team).

{% hint style="success" icon="sparkles" %}
## New: DuckLake connection

We've now implemented a function to help you connect directly to the "data lake". The old snapshot method will still work (for now), but for the very latest data, including some `silver` tables, try the following.
{% endhint %}

To connect to the database for the first time, run the following in a new notebook:

```python
from notebooks.utilities import connect_to_camino
con = connect_to_camino()
```

Once you've connected, you can [interact via SQL](https://docs.marimo.io/guides/working_with_data/sql/#example) (choose SQL cells) or in Python using the [DuckDB Python library](https://duckdb.org/docs/stable/clients/python/overview), or with the [visual database explorer on the sidebar](https://docs.marimo.io/guides/editor_features/panels/) of the interface. (Or a mix of all three.)

### SQL Cells

In marimo you can create a cell of type SQL which allows you to run (read-only) SQL queries against the data.

When you do this, marimo will automatically create and run a Python cell:

```python
import marimo as mo
```

(If you haven't already imported the `marimo` Python package into your session)

When using SQL cells, be sure to check that the connection option is your named connection to the Camino database:

<figure><img src="../../.gitbook/assets/Screenshot 2026-03-05 at 10.33.57.png" alt=""><figcaption></figcaption></figure>

If you named the connection `con` (i.e. ran `con = connect_to_camino()`  at the top of your notebook) then select:

> &#x20;DuckDB (con)

{% hint style="info" %}
## See also

* [marimo user documentation](https://docs.marimo.io/guides/)
* [DuckDB Python library documentation](https://duckdb.org/docs/stable/clients/python/overview)
{% endhint %}
