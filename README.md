Boilerplate for react apps using webpack/react-hot-loader
=================================================================

My own boilerplate based on wesbos [starter files](https://github.com/wesbos/Learn-Redux-Starter-Files/tree/master/learn-redux) and gaearons [react-hot-boilerplate](https://github.com/gaearon/react-hot-boilerplate/blob/master/README.md)
### For dev
 ```
 npm install
 npm start
 ```
 View on localhost:3000

### For production
 ```
 npm install
 npm run build
```
Setup a server.js and run node server.js (Our devServer is for dev)

### Notes

We use one config file for production and one for development. 

##### Dev
The development file contains mostly of the hot loading plugin, this to make it possible to update code without reloading.
##### Prod
In the production config we bundle together the files into bundle.js inside dist or publicly “static”. We use uglify to remove comments and indents.

### Npm commands
We need a few scripts:

The idea:
We run `npm run build` for making out bundle 
or `npm start` for running our devServer.
 
* "build:webpack": "SET NODE_ENV=production && webpack --config webpack.config.prod.js" →  We use this to set our env to production and run webpack with the PRODuction config file (not dev that we use as default in server.js). IMPORTANT: remove SET and the '&&' if we [work on a non-windows machine](http://stackoverflow.com/questions/11928013/node-env-is-not-recognized-as-an-internal-or-external-command-operable-comman). 
* "build": "npm run clean && npm run build:webpack" → Only run clean and then build:webpack
* "test": "NODE_ENV=production mocha './tests/**/*.spec.js' --compilers js:babel-core/register" 
* "clean": "rimraf dist" → rimraf is the rm -rf of nodejs, remove the old dist before creating a new
* "start": "node devServer.js" → start our DEVserver, this should now be used for production create a separate server that only contain a simple express.js server or w/e

##### Bullets
* Importand that `NODE_ENV` is set to development by default (`set node_env=development`) if it's not, hot loader wont work and cons will tell you that your comps don't know how to use hot loader. Just leave `NODE_ENV` alone, it just fu*ks with your dreams ... 