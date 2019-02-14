# stars5

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

 # Custom options for Rate Component
 Rating stars's displaying and logic is provided by **AppRate** component.
 It accept's working properties and you can set some options in addition:
 * **max**: quantity of stars, percentage calculates respectively (integer 1<n<13)
 * **clr_prime**: color for active stars (css color keywords, #-hexadecimal, rgb(), rgba(), hsl(), hsla())
 * **clr_second**: color for nonactive stars

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
