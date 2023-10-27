## Different types of Loops

### While

Loops through a block of code for as long as the condition is true.

```php
<?php
$num = 0;

while ($num < 10){
    $num += 1;
}
echo $num;

?>

```

### do…While

loops through the code once and then repeats as the condition is true

```php
<?php
do {
  echo "The number is: $x <br>";
  $x++;
} while ($x <= 5);
?>
```

---

### for

loops through a block a code a specified amount of times.

```php
<?php
for ($x = 0; $x <= 10; $x++) {
  echo "The number is: $x <br>";
}
?>
```

### foreach

loops through a block of code for each element on an array.

```php
<?php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $value) {
  echo "$value <br>";
}
?>
```

## BREAK

can be used to “stop” a loop.

```php
for ($x = 0; $x < 10; $x++) {
  if ($x == 4) {
    break;
  }
  echo "The number is: $x <br>";
}

while($x < 10) {
  if ($x == 4) {
    break;
  }
  echo "The number is: $x <br>";
  $x++;
}
```

# Continue

pretty much useless but its used to continue after a statement.

```php
for ($x = 0; $x < 10; $x++) {
  if ($x == 4) {
    continue;
  }
  echo "The number is: $x <br>";
}

while($x < 10) {
  if ($x == 4) {
    $x++;
    continue;
  }
  echo "The number is: $x <br>";
  $x++;
}
```

## TLDR

for- repeats a block of code a certain amount of times.

---

foreach - repeats a block of code for each value on a array

while - repeats a block of code while a statement is True

do…While - runs the block of code once and then while the statement is True.