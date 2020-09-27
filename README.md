# Tailwindcss

This is an angular project with tailwindcss

# Steps

Create project

```
ng new tailwindcss
```

Install dependencies

```
yarn add tailwindcss postcss-scss postcss-import postcss-loader@~3.0.0 @angular-builders/custom-webpack -D
```

Open your styles.scss file and add the following at the top.

```
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

Run command `npx tailwind init` and create the initial configuration.

Create the `webpack.config.js` file

```
module.exports = {
    module: {
        rules: [
            {
                test: /\.scss$/,
                loader: 'postcss-loader',
                options: {
                    ident: 'postcss',
                    syntax: 'postcss-scss',
                    plugins: () => [
                        require('postcss-import'),
                        require('tailwindcss'),
                        require('autoprefixer'),
                    ]
                }
            }
        ]
    }
};
```

Modify `angular.json`

```
{
  "architect": {
    "build": {
      "builder": "@angular-builders/custom-webpack:browser",
      "options": {
        "customWebpackConfig": {
          "path": "./webpack.config.js"
        }
      }
    },
    "serve": {
      "builder": "@angular-builders/custom-webpack:dev-server",
      "options": {
        "customWebpackConfig": {
          "path": "./webpack.config.js"
        }
      }
    }
  }
}
```
