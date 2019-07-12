# eslint-guideline
This project aims to provide guideline to be followed by JS projects in order to achieve coherent state of code.
Configuration provided here differentiates between *Production* and *Development* environments to make fast debugging more pleasant, but at the same time to ensure code quality and readability are persisted.

## Default setup

Since most of our JS applications are build in **React.js** the basic setup extends the recommended setup of [*eslint-plugin-react*](https://www.npmjs.com/package/eslint-plugin-react#recommended) as well as recommended options provided by [eslint](https://eslint.org/docs/rules/) compiler itself.

## Used plugins

In order to provide more complex code checking, these plugins are emplyed to help:

- eslint-plugin-import ([docs](https://www.npmjs.com/package/eslint-plugin-import)): enhancement of import statement checking
- eslint-plugin-jsx-a11y ([docs](https://www.npmjs.com/package/eslint-plugin-jsx-a11y)): checker of HTML elements in JSX files
- eslint-plugin-react ([docs](https://www.npmjs.com/package/eslint-plugin-react)): react specific utility checks

To make your project work using configuration in this project, you should install these plugins into your DevDependencies (npm install -D *<plugin_name>*)

## Integration with Webpack

To use different kind of configuration for distinct environments you should include specific configuration to your environment-specific webpack configuration rules:

```js
module: {
  rules: [
    {
      enforce: 'pre',
      test: /\.jsx?$/,
      use: [
        {
          loader: 'eslint-loader',
          options: {
            configFile: path.join(BASE_PATH, '.eslintrc-dev.json')
          }
        }
      ],
      exclude: /(node_modules)/
    },
  ]
}
```
