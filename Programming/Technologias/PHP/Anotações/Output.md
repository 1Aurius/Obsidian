in PHP there are two ways or outputting data, Echo and Print.

---

**Everything that is outputted by PHP will be read by the html, for example.**

```php
echo "hello <br>";
```

**the <br> will be read as the break function in Html.**

## Echo

```php
echo "I'm about to learn PHP!<br>";
echo "This ", "string ", "was ", "made ", "with multiple parameters.";
```

### displaying variables

```php
$text2="yessir";
$x=1;
$y=2;
echo "Study PHP at " . $txt2 . "<br>";
echo $x + $y;
```

## Print

```php
print "Hello world!<br>";
print "I'm about to learn PHP!";
```

### displaying variables

```php
$txt2 = "yessir";
$x = 5;
$y = 4;

print "Study PHP at " . $txt2 . "<br>";
print $x + $y;

```

# **TLDR**

---

**both can output variables and such yet echo**

**can output multiple Parameters.**