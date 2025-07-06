# vue-calculator

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```


## 07/06
電卓は作れた。
refの使い方がReactと違っていたり、stateでデータをまとめて管理できる方法がわからず、詰まったので、AIにきいた。(現状やり方なさそうという印象)
AIをメンターにするのはかなりいい

### わかったこと
- vue.jsは、一つにファイルで完結していて、ちゃんとコンポーネントをわけることが出来たらかなりわかりやすい
- jsの記述をそのまま書くので、今の弱いままだとだめ・ちゃんとアルゴ式の方も進めるべき
- Reactと違って、フックスが多くない印象
- でも今のままでは、仕事として書くのは難しいので、キャッチアップすること