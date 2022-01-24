# Symfony + Tailwind CSS Example

## Install Tailwind CSS with Symfony

### Create your project

Start by creating a new Symfony project if you don't have one set up already. The most common approach is to use [the Symfony installer](https://symfony.com/download).

```sh
symfony new --webapp my-project
cd my-project
```

### Install Tailwind CSS

Install `tailwindcss` and its peer dependencies via yarn, and then run the init command to generate both `tailwind.config.js` and `postcss.config.js`.

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
    "./assets/**/*.{js,vue}",
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

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="{{ encore_entry_link_tags('app') }}" rel="stylesheet">
</head>
<body class="bg-gray-100">
  {% block body %}{% endblock %}
</body>
</html>
```

## Use this repository

Clone this repository, then run:

```sh
composer install
yarn
```

Start development:

```sh
yarn dev
# or
yarn watch

symfony server:start
```