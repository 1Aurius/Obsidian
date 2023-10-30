They can be used repeatably on a program and only executes when its called.

---

## example

```php
<?php
function writeMsg() {
  echo "Hello world!";
}

writeMsg();
?>

<?php
function writeMsg() {
  return "Hello world!";
}

print(writeMsg());
?>
```

## Strict

In PHP functions can take multiple arguments, yet there is difference, if Strict is not present, arguments can be a different data type then the one declared.

```php
function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");

declare(strict_types=1);
//------------------------------------------------
function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
```

## Return Type Declarations

used to confirm the return value and if it is not met is will throw a fatal error.

```php
<?php declare(strict_types=1); 
function addNumbers( $a, $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
```