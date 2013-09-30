DataServer.jl
=============

Serves REST queries on static data. Data sources can be CSV files or RDBMS tables.

###Using CSV Data Sources:

Start the server as below, providing the location of CSV files and the port to listen on.
````
julia> using DataServer
julia> ds = DataFrameServer("../data", 8000)
julia> start(ds)
Morsel is listening on 8000...
````

The server can be accessed with:
- `/list`: list hosted dataset names
- `/meta/[dataset]`: provides column names, types, num rows etc.
- `/q/[dataset]`: dump all rows
- `/q/[dataset]?q=[query expression]`: return subset matching query expression

#### Query Format:
Operators supported:
- `__eq__`
- `__lt__`
- `__lte__`
- `__gt__`
- `__gte__`
- `__and__`
- `__or__`

Examples:
- `Total__lte__100`
- `(Sr__lt__100)__and__((Total__gt__600)__or__(Total__lt__200))`


#### TODO:
- JSON protocol wrapping all responses.
- Templates for formatting responses.
- Default display pages to show tabular data.

