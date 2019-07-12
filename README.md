# Setup Node js with Typescript

## Steps:

### Initialize node application

First step is to initialize the node application and installing typescript package

```bash
npm init
npm install typescript -s
```

### Set up Typescript

Node js runs Javascript and not Typescript. So we need to install a package `tsc` (which is an official package by Microsoft) which will transpile our `.ts` to `.js` scripts. 
For this, we'll modify our `package.json` and add this script.

``````json
"scripts": {
    "tsc": "tsc"
}
``````

We can now generate `tsconfig.json` by running the following command

```bash
npm run tsc -- --init
```

I went ahead and changed output directory for Javascript to `./build`.

![1562963214737](.\img\tsconfig_modification.png)

### Install Express JS

Next step is installing Express js and it's respective typescript package so Typescript can recognize the Express types.

```bash
npm install express -s
npm install @types/express -s
```

And we can now go ahead and create our 

[app.ts]: ./src/app.ts

 file. 

### Compile and run the application

After compiling, we can run the following script to transpile Typescript to Javascript. It'll create respective Javascript files in `./build` directory. 

```bash
npm run tsc
```

We can run the transpiled file by

```bash
node build/app.js
```

### Adding some useful scripts

We can run Typescript by installing the package `ts-node-dev`

```bash
npm install ts-node-dev -s
```

and update the `package.json` by adding two more scripts.

```json
"scripts": {
    "dev": "ts-node-dev --respawn --transpileOnly ./src/app.ts",
    "prod": "tsc && node ./build/app.js"
},
```

Now we can run the application by using following commands

```bash
# To run in development environment
npm run dev
# To run in production environment
npm run prod
```

