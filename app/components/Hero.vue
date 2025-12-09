<script setup lang="ts">
    const { isHomepage, headline, text, bgImage, buttons } = defineProps({
      isHomepage: {
        type: [Boolean, null],
        default: false
      },
      headline: [String, null],
      text: [String, null],
      bgImage: String,
      buttons: [Array, null]
    })
</script>

<template>
  <div :class="`${isHomepage ? 'h-[574px] lg:h-[890px] ' : 'h-[242px] lg:h-[525px]'} relative`">
    <img
        class="w-full h-full object-cover"
        :src="bgImage"
        alt="Hero"
    >
    <div class="absolute top-0 left-0 w-full h-full bg-gray-900 opacity-50"></div>
    <div class="absolute top-0 left-0 w-full h-full flex justify-center items-center">
        <div class="text-white text-center flex flex-col gap-5">
            <h1 class="text-4xl font-serif lg:text-8xl">{{ headline }}</h1>
            <p class="text-base font-normal lg:text-2xl">{{ text }}</p>

            <div v-if="buttons && buttons.length > 0" class="flex gap-3 justify-center flex-col mt-20 lg:flex-row">
                <button v-if="buttons[0]" class="py-4 px-6 text-gray-500 bg-white uppercase">{{ buttons[0] }}</button>
                <button v-if="buttons[1]" class="py-4 px-6 text-gray-500 border border-white text-white uppercase">{{ buttons[1] }}</button>
            </div>
        </div>
    </div>
  </div>
</template>