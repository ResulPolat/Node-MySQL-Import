# node-MySQL-importer

### DESCRIPTION

Makes it very easy to import .sql files of any size without a hassle.

### HOW IT WORKS
Unlike some other libraries that have been seen out there in the wild, this module does not parse .sql files in to chunks of seperate queries, instead it uses the binaries already availiable on the machine.

### SUPPORTED OS PLATFORMS
- windows (gets the binary location directly from MySQL)
- linux (uses 'mysql' command)
- mac (uses 'mysql' command)

### EXAMPLE USAGE
```javascript
const MySQLImporter = require('./index.js');


// setup
var test = new MySQLImporter('localhost', 3306, 'root', 'password', 'database', 'test.sql');

test.init()
    .then(test.dropDatabaseIfExists)
    .then(test.createDatabaseIfDoesNotExist)
    .then(test.execute)
    .then(function(success){
        console.log('success');
        console.dir(success);
    })
    .catch(error => {
        console.log('error');
        console.dir(error);
    })
```