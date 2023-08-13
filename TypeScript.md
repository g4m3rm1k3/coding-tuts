why use TypeScript
	1.  It helps catch errors during development
		1. with javascript you get an error only when running the code
	2. Type annotations analyze our code
	3. Only active during development

## Install TypeScript
`npm install -g typescript tsc-node`
run the help command to ensure installation
`tsc --help`
run this command to install types
`npm install @types/node`

## Typescript example
lets use a fake JSON api to try typescipt
[`jsonplaceholder.typicode.com` ](https://jsonplaceholder.typicode.com)

lets create a new project folder
`mkdir fetchjson`
change into the project directory
`cd fetchjson`
then lets initialize a our project
`npm init -y`
Now lets install axios
`npm install axios`

now lets create a file called index.ts inside the project folder
import axios at the top of the file and create a variable with the url 
```ts
import axios from 'axios';
const url = 'https://jsonplaceholder.typicode.com/todos/1';
```

Now lets make a call to the api and print out the reponse data
```ts
import axios from 'axios';
const url = 'https://jsonplaceholder.typicode.com/todos/1';
axios.get(url).then((response) => {
  console.log(response.data);
});
```
lets run the compiler on the file
`tsc index.ts`
this creates a index.js file in the folder
![[Pasted image 20230811055007.png]]
run this with node 
`node index.js`
and the output is
![[Pasted image 20230811054508.png]]
We can consolidate these two steps into one with the command 
`ts-node index.ts`
This will create the javascript file and run it
