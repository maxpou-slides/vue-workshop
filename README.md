# [Vue.js Workshop](https://github.com/maxpou-slides/vue-workshop)

[![Build Status](https://travis-ci.org/maxpou-slides/vue-workshop.svg?branch=master)](https://travis-ci.org/maxpou-slides/vue-workshop)

In a nutshell: Vue.js (pronounced “view”) could be the 'V' in an MV* pattern. The reason why this framework is gaining popularity the last years is his straightforward syntax. Such as React, Vue.js is oriented component but with a far lower barrier of entry (don't need to learn JSX). Indeed, Vue's syntax will probably look familiar to anyone who has worked with Angular/Mustache in the past.

For this workshop we will learn about Vue.js. Don't worry if you are a beginner, the tutorial can be followed by people new too!

**Warning**: this workshop uses the **StackOverflow API** which is subject to [Rate Limit (10.000 requests per IP per day)](https://api.stackexchange.com/docs/throttle). This limit can be reach easyly with the Webpack's Hot-reload module.

## Links

* [Slides](http://slides.maxpou.fr/vue-workshop/)
* Workshop
  * [Instructions](http://slides.maxpou.fr/vue-workshop/_book/)
  * [Workshop app repository + solutions (github.com/maxpou-slides/vue-workshop-app)](https://github.com/maxpou-slides/vue-workshop-app)
  * [Workshop final app](http://slides.maxpou.fr/vue-workshop-app/)


## Topics

* Exploring Vue.js basics (including templates, components) and his ecosystem (HTTP calls, routing and state management)
* Create an app based on StackOverflow API


## Pre-requisites

* Bring your own laptop with Git, NPM and your favourite Text editor / IDE installed
  * (optional) VS Code Plugin: [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
  * (optional) Atom Plugin: [language-vue](https://atom.io/packages/language-vue)
* Browser devtools
  * [Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  * [Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
* (optional) vue-cli installed
  ```bash
  $ npm install -g @vue/cli
  # or
  $ yarn global add @vue/cli
  ```


## Agenda

* Vue.js overview
  * a progressive framework
  * declarative rendering
  * virtual DOM
  * .vue files & separation of concerns
  * devtools ❤️
* Syntax
  * Conditional rendering (`v-if`, `v-else`, `v-show`)
  * loops (`v-for`)
  * forms (`v-model`)
* A world of components
  * what's a component?
  * component properties
  * computed properties
  * communication between components (event & properties)
  * lifecycle
* Vue ecosystem
  * HTTP (with [axios](https://github.com/mzabriskie/axios))
  * Routing (with [vue-router](https://router.vuejs.org/en/))
  * State Management (with [Vuex](https://vuex.vuejs.org/en/))


## Slides installation

```bash
# Don't forget the --recursive option to pull reveal.js
$ git clone https://github.com/maxpou-slides/vuejs-training --recursive
# Install&run gitbook
$ npm i && npm run doc:build
```