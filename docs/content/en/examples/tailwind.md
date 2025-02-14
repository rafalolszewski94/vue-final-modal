---
title: Tailwind usage
description: 'Vue Final Modal is a renderless, stackable, detachable and lightweight modal component.'
category: Examples
position: 10
---

## Write a `HOC`

<alert>

You can create a `higher-order component` easily and can customize `template`, `script` and `style` based on your needs.

</alert>

### VTailwindModal.vue

<show-code>

```vue
<template>
  <vue-final-modal
    v-bind="$attrs"
    classes="flex justify-center items-center"
    content-class="relative flex flex-col max-h-full mx-4 p-4 border dark:border-gray-800 rounded bg-white dark:bg-gray-900"
    v-on="$listeners"
  >
    <template v-slot="{ params }">
      <span class="mr-8 text-2xl font-bold ">
        <slot name="title"></slot>
      </span>
      <div class="flex-grow overflow-y-auto">
        <slot v-bind:params="params"></slot>
      </div>
      <div class="flex-shrink-0 flex justify-center items-center pt-4">
        <button class="vfm-btn" @click="$emit('confirm', close)">
          confirm
        </button>
        <button class="vfm-btn" @click="$emit('cancel', close)">
          cancel
        </button>
      </div>
      <button class="absolute top-0 right-0 mt-2 mr-2" @click="close">
        <mdi-close></mdi-close>
      </button>
    </template>
  </vue-final-modal>
</template>

<script>
export default {
  name: 'VTailwindModal',
  inheritAttrs: false,
  methods: {
    close() {
      this.$emit('input', false)
    }
  }
}
</script>
```

</show-code>

## How to use VTailwindModal

### Default Example

<hoc-example-tailwind></hoc-example-tailwind>

<show-code class="pt-4">

```vue
<template>
  <div>
    <v-tailwind-modal v-model="show" @confirm="confirm" @cancel="cancel">
      <template v-slot:title>Hello, vue-final-modal</template>
      <p>
        Vue Final Modal is a renderless, stackable, detachable and lightweight
        modal component.
      </p>
    </v-tailwind-modal>

    <button class="vfm-btn" @click="show = true">Open modal</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    show: false
  }),
  methods: {
    confirm() {
      // some code...
      this.show = false
    },
    cancel(close) {
      // some code...
      close()
    }
  }
}
</script>
```

</show-code>

### Custom Transition Example

<hoc-example-tailwind-custom-transition></hoc-example-tailwind-custom-transition>

<show-code class="pt-4">

```vue
<template>
  <div>
    <v-tailwind-modal
      v-model="show"
      @confirm="confirm"
      @cancel="cancel"
      :transition="{
        'enter-active-class': 'transition duration-200 ease-in-out transform',
        'enter-class': 'translate-y-full',
        'enter-to-class': 'translate-y-0',
        'leave-active-class': 'transition duration-200 ease-in-out transform',
        'leave-to-class': 'translate-y-full',
        'leave-class': 'translate-y-0'
      }"
    >
      <template v-slot:title>Hello, vue-final-modal</template>
      <p>
        Vue Final Modal is a renderless, stackable, detachable and lightweight
        modal component.
      </p>
    </v-tailwind-modal>

    <button class="vfm-btn" @click="show = true">Open modal</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    show: false
  }),
  methods: {
    confirm() {
      // some code...
      this.show = false
    },
    cancel(close) {
      // some code...
      close()
    }
  }
}
</script>
```

</show-code>
