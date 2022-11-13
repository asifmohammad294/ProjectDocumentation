<h1 style="text-align:center">PHP Guide</h1>


- to query between php and sql database
```php
$query = "insert into users(username, password) values ('$username', '$password')";
$result = mysqli_query($connection, $query);
```

- protection against sql injection in php
```php
$username = mysqli_real_escape_string($connection, $username);
```