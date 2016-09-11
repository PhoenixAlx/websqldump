![WebSQLDump Logo](https://raw.githubusercontent.com/sdesalas/websqldump/master/img/logo.whitebg.420px.png)

An ultra-light JS library for exporting data out of WebSQL


## Usage

```
// Export whole db to console
websqldump.export({
  database: 'NorthwindLite'
});
```

```
// Export database data and POST to remote server
websqldump.export({
  database: 'NorthwindLite',
  dataonly: true,
  linebreaks: true,
  success: function(sql) {
    $.ajax({type: 'POST', url: 'http://myserver.com/sync', data: {clientId: '4EAB0319', localdb: sql});
  }
});
```

```
// Export single table (schema only) to alert window, ignore errors
websqldump.export({
  database: 'NorthwindLite',
  table: 'Orders',
  schemaonly: true,
  linebreaks: true,
  success: function(sql) {
    alert(sql); 
  },
  error: function(msg) {
    // do nothing
  }
});
```

### Export options

- **database**: Required. The name of the database to export
- **table**: The table to export, if undefined then all tables are exported (defaults to undefined)
- **version**: The version of the web database (defaults to '1.0')
- **dbsize**: The size of the database in bytes (defaults to 5 * 1024 * 1024 - ie 5MB)
- **linebreaks**: Set to true to add line-breaks (defaults to false)
- **schemaonly**: Set to true to get the schema only (defaults to false)
- **dataonly**: Set to true to get the data only (defaults to false)
- **success**: Callback with 1 parameter (sql output). If not available will output to console.
- **error**: Callback with 1 parameter (err message). If not available on error will throw an exception.

### Dependencies

No JavaScript library dependencies. Requires browser with HTML5 WebSql support (such as WebKit browsers like chrome and safari) or equivalent `openDatabase` polyfill. 

### Demo

The following page contains a test harness:

[http://sdesalas.github.io/websqldump](http://sdesalas.github.io/websqldump)

You will need to create some tables and enter data in order for the demo to become meaningful.
