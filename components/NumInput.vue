<template>
  <input
    class="rounded-lg text-xl text-center w-24 h-12 bg-gray-400"
    v-model="val"
    v-on:input="change($event.target.value)"
  />
</template>

<script lang="ts">
import Vue from 'vue'

const NUMBER_FILTER_REGEX = new RegExp('[0-9]')

let lastVal = ""

export default Vue.extend({
  name: 'NumInput',
  data() {
    return {
      val: ""
    }
  },
  methods: {
    change(value: string) {
      let newVal = Number(
        value
          .split('')
          .filter((chr) => NUMBER_FILTER_REGEX.test(chr))
          .splice(0, 5)
          .join('')
      ).toString()
      this.val = newVal
      if (lastVal != newVal) {
        this.$emit('input', Number(this.val))
      }
      lastVal = newVal
    }
  }
})
</script>
