# Symfony + Tailwind CSS Example

The goal of this repository is to make itself obsolete. As long as there is no framework guide for Symfony in the Tailwind CSS docs yet (see [PR #1131](https://github.com/tailwindlabs/tailwindcss.com/pull/1131)), this repository bridges the gap between the Symfony framework and Tailwind CSS.

## Install Tailwind CSS with Symfony

### Create your project

Start by creating a new Symfony project if you don't have one set up already. The most common approach is to use [the Symfony installer](https://symfony.com/download).

```sh
symfony new symfony-tailwind --full
cd symfony-tailwind
composer require symfony/webpack-encore-bundle
yarn install
```

### Install Tailwind CSS

Install `tailwindcss` and its peer dependencies via yarn and create your `tailwind.config.js` file.

```sh
yarn add tailwindcss postcss postcss-loader autoprefixer --dev
npx tailwindcss init -p
```

### Add Tailwind to your Webpack Encore configuration

In your `webpack.config.js` file, enable the PostCSS loader.

```js
// webpack.config.js

Encore
    // ...
    .enablePostCssLoader()
;
```

### Configure your template paths

Add the paths to all of your template files in your `tailwind.config.js` file.

```js
// tailwind.config.js

module.exports = {
  content: [
    "./assets/**/*.js",
    "./assets/**/*.vue",
    "./templates/**/*.html.twig",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Add the Tailwind directives to your CSS

Add the `@tailwind` directives for each of Tailwind's layers to your `./assets/styles/app.css` file.

```css
/* app.css */

@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Start your build process

Run your build process with `yarn watch`.

```sh
yarn watch
```

### Start using Tailwind in your project

Make sure your compiled CSS is included in the `<head>` then start using Tailwind's utility classes to style your content.

## Use this repository

Clone this repository, then run:

```sh
composer install
yarn install
```

Start development:

```sh
yarn dev
# or
yarn watch

symfony server:start
```
