# Panda

Panda is a rapid prototyping framework that is build off of two of the best Node.js frameworks: [Express](http://expressjs.com) and [Moleculer](https://moleculer.services). 

The primary objective of Panda is to give you a starting point to start building your applications without a lot of setup. Panda is opiniated, but with a lot of room to customize.

Here are some of the base features you'll have out-of-the-box:
* Express routing and middleware
* Moleculer microservices API 
* EJS templating engine
* An authentication system, complete with register, login and logout routes

## Custom Capabilities

Out-of-the-box, you'll be able to start creating your site with the following building blocks:
* Routes - write Express routes quickly and easily
* Services - build an API using the Moleculer microservices framework
* Public Directory - drop in your images, js, css, etc.
* Views - create EJS templates to be rendered via your routes

## Installation

### Dependencies

To run Panda, you'll need to install the following:
* Node.js
* NPM
* MongoDB

### Quick Start

Create your Node.js project using NPM
```bash
npm init
```

Install Panda as an NPM module
```bash
npm install --save AdamPuzio/panda
```

Run Panda
```js
npx panda
```

That's it. You now have a working instance of Panda.

### Configuration

Panda doesn't need any configuring to run, but you can create a `panda.config.js` or `panda.config.json` file in your main directory.

Here are the potential values, along with defaults:

```json
{
  MONGO_URI: 'mongodb://localhost/panda',
  JWT_TOKEN: 'panda',
  
  APP_PATH: 'app',
  
  site: {
    name: 'Panda',
    desc: '',
    logo: null,
    includes: {
      header: {
        js: [],
        css: []
      },
      footer: {
        js: [],
        css: []
      }
    },
    nav: []
  }
}
```

## Application Directory Structure

```
package.json
app
  public
  routes
  services
  templates
```

## Authentication

## ToDo

### Code Tasks

* Create a generator script to build a project using `npx`
* Build custom configuration logic
* Implement authorization system
* Implement alternative authentication strategies
* Create a `panda-sample` repo
* Change `templates` directory to `views` to match Express
* Add hooks for middleware
* Allow for .env files to be used for configuration

### Documentation Tasks

* Error classes

## License
Panda is available under the [MIT license](https://tldrlegal.com/license/mit-license).