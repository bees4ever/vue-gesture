# vue2-gesture

> **Vue2 Gesture** is a Vue.js plugin based on the plugin from https://github.com/mlyknown/vue-gesture.
 >I forked it and made it run under Vue.Js 2, because the old one only runs with Vue.Js.
 See the example for how to use this plugin, simply it's now a component so not a directive anymore
 There are a bunch of arguments you can use, i.e. tap, swipe, touchstart etc. 
 When you are in the use of the PC，"tap, longtap, touchstart" will automatically be converted to "click".

- tap — fires when the element is tapped.
- doubleTap — this pair of events can be used to detect double taps on the same element
- longTap — fires when an element is tapped and the finger is held down for more than 750ms.
- swipe, swipeLeft, swipeRight, swipeUp, swipeDown — fires when an element is swiped 
- touchstart touchmove touchend click- These equivalent to touch the primary event 


## Install

#### CommonJS

- Available through npm as `vue2-gesture`. So simply run `npm install vue2-gesture`. Then you can use it as follows:

  ``` js
  // You may use: 
    window.Vue = Vue;
  var VueGesture = require('vue2-gesture')
  Vue.use(VueGesture)
  ```

#### Direct include

- You can also directly include it with a `<script>` tag when you have Vue already included globally. It will automatically install itself, and will add a global `vueGesture`.

## Usage

#### Using the `vue2-gesture` component

You can add a single event with the `type` parameter or you add a set of events with the `types` parameter which is
a javascript array.

``` html
  <vue2-gesture :type="'touchstart'"  :call="handleComponent.bind(this,'touchstart')" >touchstart</vue2-gesture>
  <vue2-gesture :type="'touchmove'"  :call="handleComponent.bind(this,'touchmove')" ><i>touchmove</i></vue2-gesture>
  <vue2-gesture :type="'touchend'"  :call="handleComponent.bind(this,'touchend')" >touchend</vue2-gesture>
  <vue2-gesture :type="'doubletap'"  :call="handleComponent.bind(this,'doubletap')">doubleTap</vue2-gesture>
  <vue2-gesture :type="'tap'"  :call="handleComponent.bind(this,'tap')">tap</vue2-gesture>
  <vue2-gesture :type="'longTap'"  :call="handleComponent.bind(this,'longTap')">longTap</vue2-gesture>
  <vue2-gesture :type="'swipe'"  :call="handleComponent.bind(this,'swipe')">swipe</vue2-gesture>
  <vue2-gesture :type="'swipeLeft'"  :call="handleComponent.bind(this,'swipeLeft')">swipeLeft</vue2-gesture>
  <vue2-gesture :type="'swipeRight'"  :call="handleComponent.bind(this,'swipeRight')">swipeRight</vue2-gesture>
  <vue2-gesture :type="'swipeUp'"  :call="handleComponent.bind(this,'swipeUp')">swipeUp</vue2-gesture>
  <vue2-gesture :type="'swipeDown'"  :call="handleComponent.bind(this,'swipeDown')">swipeDown</vue2-gesture>
  <vue2-gesture :type="'click'"  :call="handleComponent.bind(this,'click')">click</vue2-gesture>
  <vue2-gesture :types="['swipeDown','click']"   :call="handleComponent.bind(this,'EVENT')" >swipeDown and click</vue2-gesture>

```

Where `handleComponent` is a method in your Vue.js web-application. `handleComponent` should understand this two parameters:

  ``` js
 handleComponent: function(str,e){
             // str is the second input, like 'longTap', 'touchmove', 
             // there you can pass some information to the handler 
             // e is the element itself, you may use it or not
             var html = e.srcElement.innerHTML;
             e.srcElement.innerHTML=html+" "+str;
             console.log(str);
         }
  ```

#### Configuring Recognizer Options

There are two ways to customize recognizer options such as `direction` and `threshold`. The first one is setting global options:

``` js
// change the config
vueGesture.config = {
  maxSingleTapTimeInterval: 200
}
```
#### Registering Custom Events

See `/example` for a multi-event demo. To build it, run `npm install && npm run build`.

## License

MIT

