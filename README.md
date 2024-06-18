# README
This is an example app using [TailwindCSS](https://tailwindcss.com/). It was built using [this tutorial](https://github.com/dviana19/awesome-docker-rails).

1. It uses the latest Rails version
2. It uses SQLite as database
3. It uses esbuild as builder and transpiler
4. It's configured to use Turbo by default

# Extra configuration
You don't need to do any of this, I'm just showing the steps required to fully configure this project with Tailwind.

### Add extra lib using yarn
```bash
yarn add @tailwindcss/container-queries
yarn add @tailwindcss/forms
yarn add @tailwindcss/typography
```

### Upgrade your tailwind.config.js
Your file should look like this

```javascript
const defaultTheme = require('tailwindcss/defaultTheme')

module.exports = {
  content: [
    './app/views/**/*.html.erb',
    './app/helpers/**/*.rb',
    './app/assets/stylesheets/**/*.css',
    './app/javascript/**/*.js'
  ],
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter var', ...defaultTheme.fontFamily.sans],
      },
    },
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/container-queries'),
  ]
}
```

### Running with docker
```bash
docker compose build
docker compose up
```

### Running withoud docker
```bash
./bin/dev
```

### Test if it's working
Acesss http://localhost:3000 and you should see a login page.
