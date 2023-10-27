# Constructor Function
```js
function Person(id,name,email)
{
	this.id = id;
	this.name = name;
	this.email = email;
	this.dob = new Date(dob);

	this.getBirthYear = function() {
		return this.dob.getFullYear();
	}
}

Person.prototype.getBirthYear = function() {
	return this.dob.getFullYear();
}

const Person1 = new Person(1,'pedro','email','4-9-1900');
```
# Class
```js
class Person {
	constructor(id,name,dob){
		this.id = id;
		this.name = name;
		this.dob = new Date(dob);
	}

	getBirthYear() {
		return this.dob.getFullYear();
	}
	
	getFullName() {
		return `${this.firstName} ${this.lastName}`;
	}
}
```