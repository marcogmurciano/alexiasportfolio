<template>

  <nuxt-link class="" :to="{ path: '/proyecto', query: { ind: props.id } }">
    <div class="desktop flex gap-4">
      <div class="text flex w-64 gap-2">
        <h3>
          {{ formatize(props.id + 1) }}
        </h3>
        <div class="flex flex-col">
          <h3>
            {{ array[props.id].title }}
          </h3>
          <p class="bodysmall">
            {{ array[props.id].tags }}
          </p>
        </div>
      </div>
      <div v-for="(picture, i) in array[props.id].pictures" class="w-64 h-44 overflow-hidden" v-if="!isMobile">
        <img :key="i" :src="picture" alt="not found">
      </div>
      <div class="w-64 h-44 overflow-hidden" v-else>
        <img :key="0" :src="array[props.id].pictures[0]" alt="not found">
      </div>
    </div>
  </nuxt-link>

</template>


<script setup>
const props = defineProps({
  id: Number,
  isMobile: Boolean
})

import { ref, watch } from 'vue';
import { state } from "../public/data.json";

let array = ref(state.arrayDesign);

const formatize = (i) => {
  if (i < 10)
    return `0${i}`
  else
    return `${i}`
}
</script>


<style lang="sass" scoped>

</style>