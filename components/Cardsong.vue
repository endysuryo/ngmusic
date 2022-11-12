<template>
  <figure class="bg-white h-full p-3 flex flex-row gap-3 cursor-pointer">
    <div class="relative flex flex-row">
      <img
        :src="image"
        width="100"
        height="100"
        :alt="image"
        class="rounded-lg object-cover"
      />
      <img
        src="/images/play.webp"
        width="32"
        height="32"
        :alt="image"
        class="absolute m-auto left-0 right-0 top-0 bottom-0"
      />
    </div>
    <figcaption class="flex flex-col gap-1 grow">
      <div class="w-3/4">
        <div class="text-xs text-[#334155]">{{ artist }}</div>
        <div class="text-sm text-[#334155]">{{ title }}</div>
      </div>
      <div class="flex flex-row justify-start items-center mt-auto">
        <div
          class="px-3 py-1 bg-[#10b981] rounded-full text-white text-xs mr-auto"
        >
          {{ genre }}
        </div>
        <img
          src="/images/dollar.webp"
          width="16"
          height="16"
          :alt="image"
          class="rounded-lg object-cover mr-1"
        />
        <div class="text-xs text-[#f5b014]">{{ price }}</div>
      </div>
    </figcaption>
  </figure>
</template>

<script lang="ts">
export default {
  name: 'CardSong',
  props: {
    id: {
      type: Number,
      required: true,
    },
    artist: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    genre: {
      type: String,
      required: true,
    },
    price: {
      type: String,
      required: true,
    },
  },
}
</script>
