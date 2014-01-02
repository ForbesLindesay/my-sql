# then-mysql

A wrapper for the MySQL driver to use promises, connection pooling and nicer APIs all round

[![Build Status](https://travis-ci.org/then/mysql.png?branch=master)](https://travis-ci.org/then/mysql)
[![Dependency Status](https://gemnasium.com/then/mysql.png)](https://gemnasium.com/then/mysql)
[![NPM version](https://badge.fury.io/js/then-mysql.png)](http://badge.fury.io/js/then-mysql)

## Installation

    npm install then-mysql

## API

To construct a new connection pool, simply run:

```js
var pool = new MySql({
  host: 'localhost',
  user: 'me',
  passowrd: 'secret'
});

pool.query('SELECT 1 + 1 AS solution').done(function (result) {
  assert(result[0].solution === 2);
  pool.dispose().done();
});
```

### pool.query(str, values)

Return a promise for an array of objects from a SQL query.  The query may optionally contain `?`s to be replaced with escaped values from `values` which should be an array.

### pool.call(name, args)

Call a database procedure.  If it returns only one set of values, that set of values is returned as an array of objects.  If it returns multiple sets of values then they are returned as an array.

e.g.

```js
pool.call(addprocedure, [1, 2]).done(function (result) {
  assert(result[0].solution === 3);
});
```

## License

  MIT