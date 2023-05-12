# Laravel Excel Export Dropdown Columns

[Laravel Excel](https://github.com/SpartnerNL/Laravel-Excel) (Maatwebsite Laravel Excel is now called Laravel Excel) 
is a simple, but elegant Laravel wrapper around PhpSpreadsheet exports and imports.

You can have dropdown columns in Laravel Excel Export

Open the example export [User Export](https://github.com/timoye/maatwebsite-laravel-excel-export-dropdown-columns/blob/master/UserExport.php)

All select options are defined in the constructor

```
    public function __construct()
    {
        $status=['active','pending','disabled'];
        $departments=['Account','Admin','Ict','Sales'];
        $selects=[  //selects should have column_name and options
            ['columns_name'=>'D','options'=>$departments],
            ['columns_name'=>'E','options'=>$status],
        ];
        $this->selects=$selects;
        $this->row_count=50;//number of rows that will have the dropdown
        $this->column_count=5;//number of columns to be auto sized
    }
```

Your column options could be from the database

```
$roles=Role::pluck('name')->toArray();
```

The registerEvents method will loop through the data in the $selects array and populate the excel export and add validation


##### Credits
This is based on a response from [here](https://stackoverflow.com/questions/59061090/maatwebsite-laravel-excel-export-columns-with-drop-down-list)
