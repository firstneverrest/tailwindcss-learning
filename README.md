# Tailwind css Learning
Tailwind is a utility-first CSS framework which is much lower-level than Bootstrap, Material UI etc. It means tailwind css is more flexible and easy to use. See more information in [tailwind css document](https://tailwindcss.com/)

## Installation
1. use `npm install tailwindcss`
2. include these three lines in src/styles.css
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
3. add script to convert styles.css to tailwind css file that include all utility classes
```
"scripts": {
  "build-css": "npx tailwindcss -i ./src/styles.css -o ./public/tailwind.css"
},
```

## Add Tailwind CSS IntelliSense
You can add Tailwind CSS IntelliSense via extension in vscode to help improve tailwind CSS writability.  

## Config
1. use `npx tailwindcss init` to create tailwind.config.js file and you can start config in that file. If you want to get every default config like all color setting, you can use `npx tailwindcss init --full` instead.
```
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
};
```

## Custom Font
In case of google font, you can use @import url from that font and includes in src/styles.css.
```css
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@200;300;400;600&display=swap');

@tailwind base;
@tailwind components;
@tailwind utilities;
```
Then, you can add custom font in tailwind.config.js 
```
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {
      fontFamily: {
        kanit: ['Kanit'],
      },
    },
  },
  variants: {
    extend: {},
  },
  plugins: [],
};
```
When you make a change in both src/styles.css and tailwind.config.js, you have to re-compile again with `npm run build-css`

## @apply Directive
Instead of writing the same tailwind css in every the same type of component like card, you can use @apply to make it reusable.
```css
@tailwind base;
@tailwind components;
@tailwind utilities;

.card {
  @apply px-16 py-4 mx-4 bg-white shadow rounded;
}
```