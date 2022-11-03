---
theme: ./theme
title: "Nuxt 3 - More than Vue 3 on Steroids"
website: lichter.io
handle: TheAlexLichter
favicon: https://lichter.io/img/me@2x.jpg
highlighter: shiki
lineNumbers: true
layout: intro
---

# <span class="text-[#00dc82]">Nuxt</span> 3 <logos-nuxt-icon class="text-xl" />

## <span class="text-[#80eec0]">More</span> Than Vue 3 on Steroids

### JetBrains JavaScript Day 2022

<style>
  h1 {
    @apply !text-5xl;
  }

  h2 {
    @apply !text-2xl !my-16;
  }

  h3 {
    @apply !text-xl
  }
</style>

---
layout: two-cols
heading: About me
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
<img
  class="w-75 rounded-full"
  src="https://lichter.io/img/me@2x.webp"
  />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>
<VClicks class="space-y-2 mt-10 text-xl h-full">

- <mdi-account-check class="text-green-100" /> **Web Development Consultant**
- <mdi-microphone /> Speaker & Instructor
- <logos-nuxt-icon /> Nuxt.js Maintainer
- <mdi-twitter class="text-blue-400" /> @TheAlexLichter
- <mdi-web /> [https://lichter.io](https://lichter.io)
- <mdi-github /> [manniL](https://github.com/manniL)

</VClicks>
</template>

---
layout: intro
preload: false
clicks: 1
---

<h1 class="mt-12 flex justify-center items-center">

<logos-vue v-motion class="text-8xl" :initial="{ x: -500 }" :enter="{ x: 0, transition: { duration: 500 } }"/>
<mdi-heart v-if="$slidev.nav.clicks === 0" class="text-8xl invisible"/>
<mdi-heart v-if="$slidev.nav.clicks === 1" v-motion :initial="{ x: 500 }" :enter="{ x: 0, transition: { duration: 500 } }" class="text-red-500 text-8xl" />

</h1>

<!--
* Vue is a lightweight and powerful component-level framework
* But when your project grows, you often want more than "just an SPA"
-->

---
layout: intro
preload: false
---

<h1 v-motion :initial="{ y: 0 }" :enter="{ y: -500, transition: { duration: 750, delay: 250 } }" class="mt-12 flex justify-center items-center">

<logos-vue class="text-8xl"/>
<mdi-heart class="text-red-500 text-8xl" />

</h1>

---
layout: intro
preload: false
clicks: 1
---

<h1 class="mt-12">

<logos-nuxt-icon class="text-10xl" :class="$slidev.nav.clicks === 1 && 'transition ease-in-out animate-ping'" :style="$slidev.nav.clicks === 1 && 'animation: ping 2s cubic-bezier(0, 0, 0.2, 1) 3 !important;'" v-motion :initial="{ y: 500 }" :enter="{ y: 0, transition: { duration: 500, delay: 250 } }"/>

</h1>

---
preload: false
---

# Nuxt.js

<div class="absolute left-98 top-34">
<logos-nuxt-icon v-motion class="text-10xl" :initial="{ y: 0, x: 0, scale: 1.0 }" :enter="{ y: -176, x: -280, scale: 0.3, transition: { duration: 750, delay: 250 } }"/>
</div>

<Grid class="mt-16 gap-x-8">
<VClicks class="space-y-4">

- **Progressive** framework 💡
- Based on Vue 3 <logos-vue /> and Vite <logos-vitejs />
- Written in TypeScript <logos-typescript-icon />
- Performant and lightweight out of the box 📦

</VClicks>

<VClicks class="space-y-4">

- Versatile - SPA / SSG / SSR / ISR 🃏
- Universal deployment 🆙
- Optimized for cold start and serverless ⚡️
- Easily Extensible ⚙️

</VClicks>
</Grid>

---

# Folder structure

<VClicks>

- No folders by default
- Easy to get started and to prototype applications
- Supercharged directory structure available

</VClicks>

<div class="justify-around items-center flex mt-4">
<VClicks>

<img src="/nuxt-minimal-ts.png" alt="Minimal folders needed" class="h-30">

<img src="/nuxt-folders.png" alt="More Nuxt folders" class="h-70">

</VClicks>
</div>

---

# Creating Routes

<VClicks>

- You create routes by adding `.vue` files into the `/pages` folder!
- PHP-vibes (in a good way)? Yes 🎉

</VClicks>

<Grid>
<Code file="file structure" v-click>

```sh
pages/
--| hello.vue
--| articles/
----| [slug].vue
```

</Code>
<Code file="generated routes" v-click>

```json
[
  {
    "path": "/hello",
    "component": "pages/hello.vue"
  },
  {
    "path": "/articles/:slug",
    "component": "pages/articles/[slug].vue"
  }
]
```

</Code>
</Grid>

<VClicks>

- You can use parameters in parts of the route name, e.g. `artists-[group].vue`
- Nesting with folders is also possible

</VClicks>

---

# Route parameters and programmatic usage

<VClicks>

- Accessing the route parameters defined through the files is important
- You can do so via `$route` in the template

</VClicks>

<Grid class="mb-12">
<Code v-click file="/pages/artists-[group].vue">

```vue
<template>
  <h1>Group: {{ $route.params.group }}</h1>
</template>
```

</Code>

<Code v-click file="example.com/artists-rock">

```html
<h1>Group: rock</h1>
```

</Code>
</Grid>

<VClicks>

- But you can also use the `useRoute` composable

</VClicks>

<Code v-click file="/pages/artists-[group].vue">

```vue
<script setup>
const route = useRoute();
const group = route.params.group;

console.log(group);
</script>
```

</Code>

---

# `<NuxtLink>`

<VClicks>

- When navigating in our application, do not use `<a>`
- Neither `<RouterLink>`
- But `<NuxtLink>`
  - which inherits from the `vue-router` link
  - and gives some benefits like page prefetching
- It also handles external links now!
- You specify the path or URL via `to` prop

</VClicks>

<Code v-click file="pages/about.vue">

```vue
<template>
  <NuxtLink to="/about"> About page </NuxtLink>
</template>
```

</Code>

---

# Auto imports

- Show component auto import
- Show composables auto import

---

# Nuxt Content

- Show Nuxt content module basics
- .md file, routing, maybe document driven?

---

# Nitro(pack)

- Huge difference to classic Vue
- Nuxt's server engine
- Responsible for deployment, routing and API
- Can be used to implement endpoints and middleware on the server-side
- Powered by [`h3`](https://github.com/unjs/h3/) under the hood

---

# SSR / SSG / Hybrid

- SSR/SSG chosen based on simple command
- SSR = Can be hybrid now thanks to page rules!

<!-- TODO: Show page rules -->

---

# Deployment

- Seamless on over 10+ platforms
- Five of them zero-config
  - Deployment takes less than 10 minutes
- From simple Node.js support over serverless and workers to Vercel and Netlify
- Own preset can be developed - any platform could be supported

# Outlook

<VClicks>

- Runtime config
- Layouts
- Error handling (coarse- to fine-grained)
- Page-level and layout-level transitions
- Data fetching
- State management
- Nuxt plugins and modules
- Dealing with assets
- ...and more!

</VClicks>

---

# Summary

<!-- TODO Summary  -->

---
layout: intro
---

# Thanks a lot to my sponsors!

<img src="/sponsors.svg" class="h-70 mx-auto" alt="My GitHub sponsors">

---
layout: two-cols
heading: Thank you for your attention!
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
<img
  class="w-75 rounded-full"
  src="https://lichter.io/img/me@2x.webp"
  />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>

- <mdi-account-check class="text-green-100" /> **Web Development Consultant**
- <mdi-microphone /> Speaker & Instructor
- <logos-nuxt-icon /> Nuxt.js Maintainer
- <mdi-twitter class="text-blue-400" /> @TheAlexLichter
- <mdi-web /> [https://lichter.io](https://lichter.io)
- <mdi-github /> [manniL](https://github.com/manniL)

</template>

<style>
  ul {
    @apply space-y-2 mt-10 text-xl h-full;
  }
</style>

---
layout: intro
---

# Slides / Repo

- Slides: [https://lichter.link/jetbrains-js-day-2022-slides/](https://lichter.link/jetbrains-js-day-2022-slides/)
- Repo: [https://lichter.link/jetbrains-js-day-2022-repo/](https://lichter.link/jetbrains-js-day-2022-repo/)
