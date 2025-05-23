---
title: ন্যাভবার
---

:::tip[স্বয়ংক্রিয়ভাবে সাইট প্রিফিক্স যোগ করুন]
সমস্ত লিঙ্ক স্বয়ংক্রিয়ভাবে যোগ করা হবে [`base`](https://svelte.dev/docs/kit/$app-paths#base)
:::

:::important[পরম পাথ মোড ব্যবহার করুন]
অনুগ্রহ করে [`paths.relative`](https://svelte.dev/docs/kit/configuration#paths) `false` তে সেট করুন

```js title="svelte.config.js"
import adapter from '@sveltejs/adapter-static'

/** @type {import('@sveltejs/kit').Config} */
const config = {
  kit: {
    paths: {
      relative: false, // [svp! ++]
    },
  },
}

export default config
```
:::

## পরিচিতি

ন্যাভবার কনফিগ করতে থিম ডিফল্টে `navbar` অপশন প্রোভাইড করুন

প্রতিটি আইটেমে এই props থাকতে পারে:

* `title` - লেবেলের লেখা
* `to` - লিংক অ্যাড্রেস
* `icon`
  একটি HTML স্ট্রিং। যা `title` এর পরিবর্তে html কন্টেন্ট দেখাবে। এটি ন্যাভবারে কাস্টম আইকন দেখানোর জন্য উপকারী। যেমন, ন্যাভবারে টুইটারের একটি svg icon এরকম হবে
  ```js
  const twitterNavItem = {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
        <path fill="currentColor" d="M22.46 6c-.77.35-1.6.58-2.46.69c.88-.53 1.56-1.37 1.88-2.38c-.83.5-1.75.85-2.72 1.05C18.37 4.5 17.26 4 16 4c-2.35 0-4.27 1.92-4.27 4.29c0 .34.04.67.11.98C8.28 9.09 5.11 7.38 3 4.79c-.37.63-.58 1.37-.58 2.15c0 1.49.75 2.81 1.91 3.56c-.71 0-1.37-.2-1.95-.5v.03c0 2.08 1.48 3.82 3.44 4.21a4.22 4.22 0 0 1-1.93.07a4.28 4.28 0 0 0 4 2.98a8.521 8.521 0 0 1-5.33 1.84c-.34 0-.68-.02-1.02-.06C3.44 20.29 5.7 21 8.12 21C16 21 20.33 14.46 20.33 8.79c0-.19 0-.37-.01-.56c.84-.6 1.56-1.36 2.14-2.23Z"/>
    </svg>`,
    to: 'https://twitter.com/'
  }
  ```
* `external` - আইটেম কি এক্সটার্নাল লিংক কিনা তা নির্ধারণ করে
* `items` - সাব লিংক

:::note[শুধু এক লেভেল]{icon=carbon:tree-view-alt}
বর্তমান অবস্থা অনুযায়ী ন্যাভবারে শুধু এক-লেভের সাব লিংক থাকতে পারে।
:::

## উদাহরণ

```ts title="vite.config.(js|ts)"
import { defaultTheme } from '@sveltepress/theme-default'
import { sveltepress } from '@sveltepress/vite'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [
    sveltepress({
      theme: defaultTheme({
        navbar: [
          {
            title: 'Foo page',
            to: '/foo/'
          },
          {
            title: 'With dropdown',
            items: [
              {
                title: 'Bar page',
                to: '/bar/'
              },
              {
                title: 'External Github page',
                to: 'https://github.com/',
                external: true
              }
            ]
          }
        ]
      })
    })
  ]
})
```
