# 🐛 Report 🐛

Something is broken between vite, tsc, swc, and js-big-decimal.

# To reproduce

Steps taken in this repo:

- `yarn create vite`
  - react
  - Typescript + SWC
- `yarn add js-big-decimal`
- add `bigDecimal` import to `App.tsx` (lines 5, 8, and 27)

# Observed Behaviour

`yarn dev` serves a blank page. Console shows

```
Uncaught ReferenceError: global is not defined
    js js-big-decimal.js:9
    __require chunk-RSJERJUL.js:3
    <anonymous> js-big-decimal.js:804
js-big-decimal.js:9:31
```

# Notable

The _wrong file_ is being imported. `js-big-decimal.js` in the above error is `localhost/node_modules/js-big-decimal/dist/node/js-big-decimal.js`, where it should be `localhost/node_modules/js-big-decimal/dist/web/js-big-decimal.js`
