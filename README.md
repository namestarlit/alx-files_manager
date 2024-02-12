## 0x04. Files manager
### Files Manager

This project serves as a summary of the back-end trimester, covering authentication, NodeJS, MongoDB, Redis, pagination, and background processing.

The primary objective is to build a simple platform for uploading and viewing files, with the following functionalities:

- User authentication via a token
- List all files
- Upload a new file
- Change permission of a file
- View a file
- Generate thumbnails for images

### Learning Objectives

Upon completing this project, you should be able to explain, without the help of external resources, how to:

- Create an API with Express
- Authenticate a user
- Store data in MongoDB
- Store temporary data in Redis
- Setup and use a background worker

### Setup Files
`package.json`
```json
{
  "name": "files_manager",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "lint": "./node_modules/.bin/eslint",
    "check-lint": "lint [0-9]*.js",
    "start-server": "nodemon --exec babel-node --presets @babel/preset-env ./server.js",
    "start-worker": "nodemon --exec babel-node --presets @babel/preset-env ./worker.js",
    "dev": "nodemon --exec babel-node --presets @babel/preset-env",
    "test": "./node_modules/.bin/mocha --require @babel/register --exit"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "bull": "^3.16.0",
    "chai-http": "^4.3.0",
    "express": "^4.17.1",
    "image-thumbnail": "^1.0.10",
    "mime-types": "^2.1.27",
    "mongodb": "^3.5.9",
    "redis": "^2.8.0",
    "sha1": "^1.1.1",
    "uuid": "^8.2.0"
  },
  "devDependencies": {
    "@babel/cli": "^7.8.0",
    "@babel/core": "^7.8.0",
    "@babel/node": "^7.8.0",
    "@babel/preset-env": "^7.8.2",
    "@babel/register": "^7.8.0",
    "chai": "^4.2.0",
    "chai-http": "^4.3.0",
    "mocha": "^6.2.2",
    "nodemon": "^2.0.2",
    "eslint": "^6.4.0",
    "eslint-config-airbnb-base": "^14.0.0",
    "eslint-plugin-import": "^2.18.2",
    "eslint-plugin-jest": "^22.17.0",
    "request": "^2.88.0",
    "sinon": "^7.5.0"
  }
}
```

`.eslintrc.js`
```js
module.exports = {
    env: {
      browser: false,
      es6: true,
      jest: true,
    },
    extends: [
      'airbnb-base',
      'plugin:jest/all',
    ],
    globals: {
      Atomics: 'readonly',
      SharedArrayBuffer: 'readonly',
    },
    parserOptions: {
      ecmaVersion: 2018,
      sourceType: 'module',
    },
    plugins: ['jest'],
    rules: {
      'max-classes-per-file': 'off',
      'no-underscore-dangle': 'off',
      'no-console': 'off',
      'no-shadow': 'off',
      'no-restricted-syntax': [
        'error',
        'LabeledStatement',
        'WithStatement',
      ],
    },
    overrides:[
      {
        files: ['*.js'],
        excludedFiles: 'babel.config.js',
      }
    ]
};
```

`babel.config.js`
```js
module.exports = {
    presets: [
      [
        '@babel/preset-env',
        {
          targets: {
            node: 'current',
          },
        },
      ],
    ],
};
```

Run `npm install` when you have `package.json`

### References
[Node JS getting started](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs)  
[Process API doc](https://node.readthedocs.io/en/latest/api/process/)  
[Express getting started](https://expressjs.com/en/starter/installing.html)  
[Mocha documentation](https://mochajs.org/)  
[Nodemon documentation](https://github.com/remy/nodemon#nodemon)  
[MongoDB](https://github.com/mongodb/node-mongodb-native)  
[Bull](https://github.com/OptimalBits/bull)  
[Image thumbnail](https://github.com/OptimalBits/bull)  
[Mime-Types](https://www.npmjs.com/package/mime-types)  
[Node-Redis](https://github.com/redis/node-redis)