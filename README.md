# Using New Improved Vue-CLI v3
This is a basic example of using vue. I'm testing the newer vue cli version and it has some big changes compared to the old one.
I would recommend trying the vue ui and create your project through there!  
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