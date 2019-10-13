# [tiptap-vuetify](https://github.com/iliyaZelenko/tiptap-vuetify) with Nuxt

Play on Codesanbox: https://codesandbox.io/s/github/iliyaZelenko/tiptap-vuetify-nuxt/tree/master/

![](https://i.imgur.com/pP78Oaa.png)

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn run dev

# build for production and launch server
$ yarn run build
$ yarn start

# generate static project
$ yarn run generate
```

## Important parts

### Transpile

It is important to specify [transpile](https://nuxtjs.org/api/configuration-build/#transpile) ([link to code below](https://github.com/iliyaZelenko/tiptap-vuetify-nuxt/blob/813441ce1f0cbdcaee4c5b9f82555c399c4a8859/nuxt.config.js#L55)).

``` js
build: {
  transpile: ['vuetify/lib', 'tiptap-vuetify']
}
```

### Load icons

I put links to icon styles in [`link`](https://nuxtjs.org/api/configuration-head) array, most likely you only need your kind of icons and you can load the icons in a different way, not like below ([link to code below](https://github.com/iliyaZelenko/tiptap-vuetify-nuxt/blob/master/nuxt.config.js#L26)).

``` js
link: [
  { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' },
  // Iconfonts for Vuetify. You need to leave only which one you use
  { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900|Material+Icons' },
  { rel: 'stylesheet', href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.11.2/css/all.min.css' },
  { rel: 'stylesheet', href: 'https://cdnjs.cloudflare.com/ajax/libs/MaterialDesign-Webfont/4.4.95/css/materialdesignicons.min.css' }
]
```

### Plugin

It can be seen that I created and connected the [plugin](https://github.com/iliyaZelenko/tiptap-vuetify-nuxt/blob/master/plugins/TiptapVuetify.js).

``` js
import Vue from 'vue'
import { TiptapVuetifyPlugin } from 'tiptap-vuetify'
import 'tiptap-vuetify/dist/main.css'

export default ({ app }) => {
  Vue.use(TiptapVuetifyPlugin, {
    // Below is an IMPORTANT line.
    vuetify: app.vuetify,
    iconsGroup: 'mdi'
  })
}
```

And include it (`nuxt.config.js`):
```
plugins: [
  '~/plugins/TiptapVuetify'
],
```

Vuetify object (`new Vuetify(opts)`) is in `app.vuetify` because of `@nuxtjs/vuetify` module, if you do not use `@nuxtjs/vuetify` and initialize Vuetify yourself, then do not forget to pass the Vuetify object as in the code above. You can read more on [Vuetify's docs](https://vuetifyjs.com/en/getting-started/quick-start#default-installation).

About Nuxt's plugins [documentation here](https://nuxtjs.org/guide/plugins#codefund_ad).

---

For detailed explanation on how things work, checkout [Nuxt.js docs](https://nuxtjs.org).
