```js
//gets by id

const button1 = document.getElementById('button1');

  

//gets 1

const button2 = document.querySelector('button');

  

//gets all of tag ig lol idk

const buttons = document.querySelectorAll('button');

  

//gets all of tag

const buttons_by_tag = document.getElementsByTagName('button');

  

//remove first element

buttons[0].remove();
```
# Index
```js
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Document</title>

    <script src="https://cdn.tailwindcss.com"></script>

    <script>

        tailwind.config = {

          theme: {

            extend: {

              colors: {

                clifford: '#da373d',

              }

            }

          }

        }

      </script>

  

</head>

<body>

    <button id="button1" name="button" class=" border border-8 rounded-[12px] hover:border-sky-950  p-4 hover:text-blue-950 text-[40px] font-bold">teste1</button>

    <button id="button2" name="button" class=" border border-8 rounded-[12px] hover:border-sky-950  p-4 hover:text-blue-950 text-[40px] font-bold">teste2</button>

    <button id="button3" name="button" class=" border border-8 rounded-[12px] hover:border-sky-950  p-4 hover:text-blue-950 text-[40px] font-bold">teste3</button>

</body>

<script src="/js/script1.js">

  

</script>

</html>
```