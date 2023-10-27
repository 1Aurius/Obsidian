# For
```js
for(let i=0; i < 10; i++){
	console.log(i)
}

for(let todo of todos){
console.log(todo.smth)
}

todo.foreach(function(todo){
console.log(todo.text)
})
```
# While
```js
let i=0
while(i<10){
	console.log(i)
	i++
}
```
# MAP
```js
	const todoText = todo.map(function(todo){
		return todo.text
	})
```