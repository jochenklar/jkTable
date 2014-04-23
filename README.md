jkTable
=======

This is a javascript table to be used with jQuery and bootstrap v3.

Usage
=====

It is used like any other jQuery plugin:
<pre>
    <div id="table"></div>
    <script type="text/javascript">
        $('#table').jk_table({
            'rowsurl': '/some/url/rows',
            'colsurl': '/some/url/cols'
        });
    </script>
</pre>

`colsurl` is a controller expected to return a json in the form 
<pre>
    [
        {"id": 0, name": "foo", "verboseName":"Foo", "width":"50px"},
        {"id": 1, name": "bar"}
    ]
</pre>

`rowsurl` is a controller expected to return a json in the form
<pre>
    {
        "nrows": 10,  // number of rows in this json
        "page": 1,    // number of the page this json contains
        "pages": 20,  // number of total pages
        "total": 100, // total number of rows
        "rows": [
            {"id": 0, "cell": ['foo','bar']},
            {"id": 0, "cell": ['foo','bar']},
            ...
        ]
    }
</pre>

Both urls will be called with the query parameters:

+ `nrows` the number of rows to be returned
+ `page` the page to be returned
+ `sort` a parameter for sorting in the form 'name ASC' or 'name DESC'
+ `search` a string to be searched (in all columns)

