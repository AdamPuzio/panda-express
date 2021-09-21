# Panda

Panda is a rapid application framework that makes spinning up new web applications quick and easy, while still allowing for scalability. 

Panda uses [Koa.js](https://koajs.com/) as a web framework and [Moleculer](https://moleculer.services/) as a microservices framework. Using these together allows you to create truly powerful, flexible and scalable applications that can be easily run on a developer's local machine or across an entire distributed architecture of nodes. It aims to provide convenience while still remaining unopinionated. The power is yours to create what you want. 

Once you're set up, you have access to the following out-of-the-box:
- Services
- Routes
- Views
- Public Directory

All of this can be expanded using the built-in Package system. 

## Installation & Setup

Setting up Panda is easy:

```bash
npm init -y
npm install --save panda
npx panda create app
npx panda run
```

Seriously, it's that easy. 

### Configuration

You can run Panda configuration-free, but when you're ready to start configuring how it works and runs, you have a number of different ways to do it. 

#### Run-Time Options

When running `npx panda run`, you have a number of options that you can use to configure your app:

`--services [services]` (default: *)

This provides the list of services to start in this node, separated by commas

Examples:
```bash
# run the www and api services
npx panda run --services www,api
# run the 
npx panda run --services www@2
```

`--repl`

When set, it starts in REPL mode

`--config [cfg]` (default: `panda.config.js`)

Point to a specific configuration file to use

`--pkgdir [dir]` (default: `node_modules`)

Set the directory to scan for Packages

`--appdir [dir]` (default: `app`)

Set the directory to scan for local files

`--loglevel [level]` (default: `debug`)

The log level to use (error/warn/info/verbose/debug/silly)

#### Config Files

As mentioned above, you can bake your own configuration file into your project. By default, it looks for `panda.config.js`, but by setting the `--config` option, you can point it to whatever file you want. 

### Alternative Installation Methods

While the installation method above is the preferred way of installing and running Panda, there are other ways you can use it. 

#### Test Setup

Want to just play around with Panda and see how easy it is to create web apps? Just clone the repo and go:

```bash
git clone https://github.com/AdamPuzio/panda.git my-app
cd my-app
npm install
npx panda run
```

#### As a Library

If you are creating your own application and want to use Panda's functionality without running it through Panda, you can simply install it via `npm install --save panda` and then require it in your own script:

```js
const panda = require('panda')
```

## Development

### Services

Panda uses Moleculer as its service broker. Any services created in the `/app/services` directory with the name `{service}.service.js` will be registered into the system.

### Routes

Panda uses Koa for routing. When creating routes in `/app/routes`, routing prefixes are assigned based on directory structure. Filenames within the directories don't matter. For example, with the following directory structure:

```
app
  routes
    index.js
    foo
      index.js
      bar.js
```

Routes within `/app/routes/index.js` will automatically be prefixed with `/`, so they'll be available at the top level. Any routes created within `/app/routes/foo/index.js` or `/app/routes/foo/bar.js` will be prefixed with `/foo/`. The filenames `index` and `bar` have no bearing on routes.

### Views

By default, Panda using ExtJS as its templating engine. You can begin adding .html template files into the `/app/views` directory and then calling them either from routes or other views.

### Public Directory

Within `/app/public` you can serve any static content you'd like. Just drop a file into that directory and it'll immediately be available at the relative path. 

### Packages

### Panda Development

When working on the core Panda library (not an application that uses Panda), install Panda in a local directory:

```bash
mkdir lib
cd lib
git clone git@github.com:AdamPuzio/panda.git
cd ../
```

Next, update your app's `package.json` file to reflect that it should use the local directory instead of the NPM version in `node_modules`:

```js
{
  ...
  "dependencies": {
    "panda": "file:./lib/panda"
  }
}
```

Finally, run `npm install` to install all Panda dependencies and ensure that it's referencing the local copy. Now, all changes made to the code in `lib/panda` will be reflected immediately. 
