---
title: API Reference
description: 'Vue Final Modal is a renderless, stackable, detachable and lightweight modal component.'
category: API
position: 7
---
## Usage

<alert>`$vfm` is an object containing VueFinalModal's data/methods.</alert>

### **Options API**

Just use `this.$vfm`.

### **Composition API** <badge>Vue 3 only</badge>

```js
import { inject } from 'vue'

export default {
  setup() {
    const $vfm = inject('$vfm')
  }
}
```
## API

### `show(name, params)`

- Type: `Function`
- Arguments:
  - name: `String` - Name of the modal
  - params: `?: object` - Any data that you want to pass into the modal, checkout the guide [params](/guide/params).

<show-code text="Example">

<v-api-show class="py-4"></v-api-show>

```js
this.$vfm.show('example', { userName: 'vue-final-modal' })
```

```html[Modal.vue]
<template>
  <vue-final-modal v-model="show" name="example">
    <template v-slot:title>$vfm.show</template>
    <template v-slot="{ params }">
      Hi {{ params.userName }}
    </template>
  </vue-final-modal>
</template>
<script>
  export default {
    data: () => ({
      show: false
    })
  }
</script>
```

<alert>`v-model` is necessary when you open a modal with `$vfm.show(name)` API.</alert>

</show-code>

### `hide([names])`

- Type: `Function`
- Arguments:
  - names: `String` - The names to hide

<show-code text="Example">

```html
<template>
  <vue-final-modal v-model="show" name="example">Vue Final Modal is awesome</vue-final-modal>
  <vue-final-modal v-model="show2" name="example2">Vue Final Modal is awesome 2</vue-final-modal>
</template>

<script>
  export default {
    data: () => ({
      show: true,
      show2: true
    }),
    mounted() {
      this.$vfm.hide('example', 'example2')
    }
  }
</script>
```

</show-code>

### `hideAll()`

hide all modals.

### `toggle(name, show, params)`

- Type: `Function`
- Arguments:
  - name: [`String` | `Array`] - The names of the modal
  - show: `?: Boolean` - Show modal or not
  - params: `?: object` - Any data that you want to pass into the modal, checkout the guide [params](/guide/params).

toggle modals by name.

### `get([names])`

- Type: `Function`
- Arguments:
  - names: `String` - Get the names of the modal instances
- Return:
  - `Array`: returns the modal instances

### `openedModals`

- Return:

  - `Array`: returns the opened modal instances.

- Examples:

1. `$vfm.openedModals[0]`: get the first opened modal instance.
2. `$vfm.openedModals.length`: get how many modals was opened.

### `modals`

- Return:
  - `Array`: returns all modal instances.
