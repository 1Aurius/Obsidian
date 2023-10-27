---
type:
---
# setting
```js
const person = {
	   firstName: 'jhon',
	   lastName:  'Doe',
	   age:        30,
	   hobbies    [1,2,3],
	   address:   {
				   street: '50 main st',
				   city:   'Boston',
				   state:  'MA'
				   }
	  }
```

```js
const person = {

    firstName: 'jhon',

    lastName:  'Doe',

    age:        30,

    hobbies:    [1,2,3],

    address:   {

                street: '50 main st',

                city:   'Boston',

                state:  'MA'

                }

}

person.gender = 'yes'

  

const todo = [person,person,person]

  

const todoJSON = JSON.stringify(todo);

console.log(todoJSON)

  

console.log(todo[1].age);
```