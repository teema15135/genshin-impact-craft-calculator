<template>
  <div class="container">
    <table>
      <tbody>
        <tr>
          <th></th>
          <td><ItemImage :star="Rarity.TWO_STAR" /></td>
          <td><ItemImage :star="Rarity.THREE_STAR" /></td>
          <td><ItemImage :star="Rarity.FOUR_STAR" /></td>
          <td><ItemImage :star="Rarity.FIVE_STAR" /></td>
        </tr>
        <tr>
          <th>Needed</th>
          <td><NumInput v-model="needed[0]" /></td>
          <td><NumInput v-model="needed[1]" /></td>
          <td><NumInput v-model="needed[2]" /></td>
          <td><NumInput v-model="needed[3]" /></td>
        </tr>
        <tr>
          <th>Have</th>
          <td><NumInput v-model="have[0]" /></td>
          <td><NumInput v-model="have[1]" /></td>
          <td><NumInput v-model="have[2]" /></td>
          <td><NumInput v-model="have[3]" /></td>
        </tr>
        <tr>
          <th>Left</th>
          <td class="text-xl">{{ left[0] }}</td>
          <td class="text-xl">{{ left[1] }}</td>
          <td class="text-xl">{{ left[2] }}</td>
          <td class="text-xl">{{ left[3] }}</td>
        </tr>
      </tbody>
    </table>
    <div>
      <div v-show="isComplete">Complete</div>
      <div v-show="!isComplete">Incomplete</div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import ItemImage, { Rarity } from '~/components/ItemImage.vue'
import NumInput from '~/components/NumInput.vue'

export default Vue.extend({
  components: {
    ItemImage,
    NumInput
  },
  data() {
    return {
      Rarity,
      needed: [1, 9, 9, 6],
      have: [0, 0, 0, 0],
      left: [0, 0, 0, 0],
      isComplete: false
    }
  },
  methods: {
    calculate: function() {
      let mNeed = this.needed.copyWithin(0, 0)
      let mHave = this.have.copyWithin(0, 0)
      this.left = [9, 8, 7, 6]
      console.log(mNeed, mHave)
    }
  },
  watch: {
    needed: function(val) {
      this.calculate()
    },
    have: function(val) {
      this.calculate()
    }
  }
})
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
