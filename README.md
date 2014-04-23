jkTable
=======

This is a javascript table to be used with jQuery and bootstrap v3.

Usage
=====

It is used like any other jQuery plugin:
```html
    <div id="table"></div>
    <script type="text/javascript">
        $('#table').jk_table({
            'rowsurl': '/some/url/rows',
            'colsurl': '/some/url/cols'
        });
    </script>
```

`colsurl` is a controller expected to return a json in the form 
```
    [
        {"id": 0, name": "foo", "verboseName":"Foo", "width":"50px"},
        {"id": 1, name": "bar"}
    ]
```

`rowsurl` is a controller expected to return a json in the form
```
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
```

Both urls will be called with the query parameters:

+ `nrows` the number of rows to be returned
+ `page` the page to be returned
+ `sort` a parameter for sorting in the form 'name ASC' or 'name DESC'
+ `search` a string to be searched (in all columns)

More documentation will follow someday ...