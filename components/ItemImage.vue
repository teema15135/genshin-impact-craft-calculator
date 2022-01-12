<template>
<div>
  {{ star.toString() }}
</div>
</template>

<script lang="ts">
import Vue, { PropOptions } from 'vue'

export enum Rarity {
  TWO_STAR,
  THREE_STAR,
  FOUR_STAR,
  FIVE_STAR
}

export default Vue.extend({
  name: "ItemImage",
  props: {
    star: {
      type: Number,
      required: true
    } as PropOptions<Rarity>
  },
  computed: {
  }
})
</script>
