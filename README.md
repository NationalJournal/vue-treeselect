# vue-treeselect
[![npm](https://badgen.now.sh/npm/v/@nationaljournal/vue-treeselect)](https://www.npmjs.com/package/@nationaljournal/vue-treeselect) [![Build](https://badgen.now.sh/circleci/github/nationaljournal/vue-treeselect)](https://circleci.com/gh/nationaljournal/vue-treeselect/tree/master) [![Coverage](https://badgen.net/codecov/c/github/nationaljournal/vue-treeselect)](https://codecov.io/gh/nationaljournal/vue-treeselect?branch=master)
![npm monthly downloads](https://badgen.now.sh/npm/dm/@nationaljournal/vue-treeselect)
![jsDelivr monthly hits](https://badgen.net/jsdelivr/hits/npm/@nationaljournal/vue-treeselect) [![Known vulnerabilities](https://snyk.io/test/npm/@nationaljournal/vue-treeselect/badge.svg)](https://snyk.io/test/npm/@nationaljournal/vue-treeselect) ![License](https://badgen.net/github/license/nationaljournal/vue-treeselect)

> A multi-select component with nested options support for Vue.js

![Vue-Treeselect Screenshot](https://raw.githubusercontent.com/nationaljournal/vue-treeselect/master/screenshot.png)

### Differences from `riophae/vue-treeselect`

- Added `aria-label` prop to input.
- Added `exclusive` prop to force one branch expanded at a time.
- Added `showSelectedChildrenCount` prop to display count of selected items under a branch node
- Automatically collapse branch node if it's selected.

### Features

- Single & multiple select with nested options support
- Fuzzy matching
- Async searching
- Delayed loading (load data of deep level options only when needed)
- Keyboard support (navigate using <kbd>Arrow Up</kbd> & <kbd>Arrow Down</kbd> keys, select option using <kbd>Enter</kbd> key, etc.)
- Rich options & highly customizable
- Supports a wide range of browsers (see [below](#browser-compatibility))
- RTL support

*Requires Vue 2.2+*

### Getting Started

It's recommended to install vue-treeselect via npm, and build your app using a bundler like [webpack](https://webpack.js.org/).

```bash
npm install --save @nationaljournal/vue-treeselect
```

This example shows how to integrate vue-treeselect with your [Vue SFCs](https://vuejs.org/v2/guide/single-file-components.html).

```vue
<!-- Vue SFC -->
<template>
  <div id="app">
    <treeselect v-model="value" :multiple="true" :options="options" />
  </div>
</template>

<script>
  // import the component
  import Treeselect from '@nationaljournal/vue-treeselect'
  // import the styles
  import '@nationaljournal/vue-treeselect/dist/vue-treeselect.css'

  export default {
    // register the component
    components: { Treeselect },
    data() {
      return {
        // define the default value
        value: null,
        // define options
        options: [ {
          id: 'a',
          label: 'a',
          children: [ {
            id: 'aa',
            label: 'aa',
          }, {
            id: 'ab',
            label: 'ab',
          } ],
        }, {
          id: 'b',
          label: 'b',
        }, {
          id: 'c',
          label: 'c',
        } ],
      }
    },
  }
</script>
```

If you just don't want to use webpack or any other bundlers, you can simply include the standalone UMD build in your page. In this way, make sure Vue as a dependency is included before vue-treeselect.

```html
<html>
  <head>
    <!-- include Vue 2.x -->
    <script src="https://cdn.jsdelivr.net/npm/vue@^2"></script>
    <!-- include vue-treeselect & its styles. you can change the version tag to better suit your needs. -->
    <script src="https://cdn.jsdelivr.net/npm/@nationaljournal/vue-treeselect@^0.5.0/dist/vue-treeselect.umd.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@nationaljournal/vue-treeselect@^0.5.0/dist/vue-treeselect.min.css">
  </head>
  <body>
    <div id="app">
      <treeselect v-model="value" :multiple="true" :options="options" />
    </div>
  </body>
  <script>
    // register the component
    Vue.component('treeselect', VueTreeselect.Treeselect)

    new Vue({
      el: '#app',
      data: {
        // define the default value
        value: null,
        // define options
        options: [ {
          id: 'a',
          label: 'a',
          children: [ {
            id: 'aa',
            label: 'aa',
          }, {
            id: 'ab',
            label: 'ab',
          } ],
        }, {
          id: 'b',
          label: 'b',
        }, {
          id: 'c',
          label: 'c',
        } ],
      },
    })
  </script>
</html>
```

### Documentation & Live Demo

[Visit the website](https://vue-treeselect.js.org/)

Note: please use a desktop browser since the website hasn't been optimized for mobile devices.

### Browser Compatibility

- Chrome
- Edge
- Firefox
- IE ≥ 9
- Safari

It should function well on IE9, but the style can be slightly broken due to the lack of support of some relatively new CSS features, such as `transition` and `animation`. Nevertheless it should look 90% same as on modern browsers.

### Bugs

You can use this [pen](https://codepen.io/riophae/pen/MExgzP) to reproduce bugs and then [open an issue](https://github.com/nationaljournal/vue-treeselect/issues/new).

### Contributing

1. Fork & clone the repo
2. Install dependencies by `yarn` or `npm install`
3. Check out a new branch
4. `npm run dev` & hack
5. Make sure `npm test` passes
6. run `npm version` to bump the version number
7. Push your changes & file a pull request
8. Manually run Publish to NPM github action if necessary (it should be triggered automatically)

### Credits

This project is inspired by [vue-multiselect](https://github.com/monterail/vue-multiselect), [react-select](https://github.com/JedWatson/react-select) and [Ant Design](https://github.com/ant-design/ant-design/). Special thanks go to their respective authors!

Some icons used in this project:

  - "link" icon made by [Smashicons](https://www.flaticon.com/authors/smashicons) is licensed under [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)
  - "spinner" icon from [SpinKit](https://github.com/tobiasahlin/SpinKit) is licensed under the [MIT License](https://github.com/tobiasahlin/SpinKit/blob/master/LICENSE)
  - "caret" icon made by [Dave Gandy](https://www.flaticon.com/authors/dave-gandy) is licensed under [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)
  - "delete" icon made by [Freepik](https://www.flaticon.com/authors/freepik) is licensed under [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)
  - "checkmark symbol" & "minus symbol" icons made by [Catalin Fertu](https://www.flaticon.com/authors/catalin-fertu) are licensed under [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)

### License

Copyright (c) 2020-present [National Journal](https://github.com/nationaljournal).

Released under the [MIT License](https://github.com/nationaljournal/vue-treeselect/blob/master/LICENSE).
