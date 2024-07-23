# Node Setup To Typescript
[[Fleeting Notes MOC]]
### SETUP
```shell
npx gitignore node
npx covgen _email_
npm init -y
```
### PACKAGE JSON
```json
{
  "name": "ts-node-express",
  "version": "1.0.0",
  "description": "",
  "main": "src/index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  ...
```
//Essentials for project
- Express
- Sequelize
- Mysql2
- Dotenv
### FOR TYPESCRIPT
```js
// src/index.js
const express = require('express');
const dotenv = require('dotenv');

dotenv.config();

const app = express();
const port = process.env.PORT;

app.get('/', (req, res) => {
  res.send('Express + TypeScript Server');
});

app.listen(port, () => {
  console.log(`[server]: Server is running at http://localhost:${port}`);
});
```
- TS Development 
	- `npm i -D typescript @types/express @types/node`
	- `npx tsc --init`
#### tsconfig
```
{
  "compilerOptions": {
    ...
    "outDir": "./dist"
    ...
  }
}
```
### RUNNING TS NODE 
- `npx ts-node src/index.ts`
### WATCHING FILE CHANGE
- `npm i -D nodemon ts-node`
```json
//package.json
{
  "scripts": {
    "build": "npx tsc",
    "start": "node dist/index.js",
    "dev": "nodemon src/index.ts"
  }
}
```
- Make nodemon.json in project roots
```js
//nodemon.json
{
  "watch": ["src"],
  "ext": "ts",
  "exec": "concurrently \"npx tsc --watch\" \"ts-node src/index.ts\""
}
```