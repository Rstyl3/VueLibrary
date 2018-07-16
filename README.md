# Using New Improved Vue-CLI v3
This is a basic example of using vue. I'm testing the newer vue cli version and it has some big changes compared to the old one.
I would recommend trying the vue ui and create your project through there!  

Vue-cli 3.x is a complete rewrite, with a lot of new awesome features. You will be able to select features like routing, Vuex or Typescript, then add and upgrade building blocks called "vue-cli plugins". But having so much more options also means the tool is now more complex and harder to start using. That's why we thought having a full-blown GUI would help discover the new features, search and install vue-cli plugins and unlock more possibilities overall while not being limited by a terminal interface. To sum up, vue-cli will not only allow you to bootstrap a new project easily, but it will also remain useful for ongoing work afterwards!

Here is a guide you could follow: https://blog.usejournal.com/getting-to-know-the-new-vue-cli-3-user-interface-a173b00128bd

### New commands to look out for are:

Upgrading your vue:
```npm
npm install -g @vue/cli
```
Creating new project:
```npm
vue create hello-world
```
Before was:
```npm
vue init webpack my-project
```
Note: You can still use this command on the new version  and create your project 

Running local server:
```npm
npm run serve
```
Before was:
```npm
npm run dev
```
Building is still the same command

## Documentation
You can find out more info how to configure your app here: https://cli.vuejs.org/

## Configuration
You can configure you webpack through creating a vue.config.js file in the root of your project.
more info here: https://cli.vuejs.org/guide/webpack.html#simple-configuration

## Ignoring some eslint warning
You can add some rules through package.json
Here is an example of ignoring console.log warning:
```json
  "eslintConfig": {
      "rules": {
      "no-console": 0
    }
  }
```
More info here: https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint#configuration

## Tweaking Webpack Config

Vue CLI provides a very easy and flexible way of tweaking the internal webpack config.

To do this, you have to use the `configureWebpack` option in [vue.config.js](https://cli.vuejs.org/config/#vue-config-js)

```javascript
// vue.config.js
module.exports = {
  configureWebpack: {
    plugins: [
      new MyAwesomeWebpackPlugin()
    ]
  }
}
```
Just in case you don’t already have the vue.config.js file in your project root. You would have to create it manually.   

You might be wondering: “How do I know what’s already in the internal Webpack config so I know what I need to add?”   
Well this is where the `vue inspect` command becomes handy. This command outputs all the internal Webpack config to your terminal.   
To output it to a file, just specify a file name like this:

```console
vue inspect > output.js
```
## Disable Hashed Filenames

While generated static asset filenames contain a hash to ensure the browser picks up changed files this can be disabled. One common scenario for this is when integrating Vue with a backend that dictates a code structure other than what Vue CLI generates, such as with WordPress or Laravel. To disable the hashed filenames, the following can be added to [vue.config.js](https://cli.vuejs.org/config/#vue-config-js):

```javascript
module.exports = {
    chainWebpack: (config) => {
    config.module
      .rule('images')
      .use('url-loader')
      .tap(options => Object.assign({}, options, { name: 'img/[name].[ext]' }));
  },
  css: {
    extract: {
      filename: '/css/[name].css',
      chunkFilename: '/css/[name].css',
    },
  },
  configureWebpack: {
    output: {
      filename: 'js/[name].js',
      chunkFilename: 'js/[name].js',
    },
  },
};
```

## Change build path

```javascript
// vue.config.js
module.exports = {
  outputDir: 'wwwroot'
}
```