<template>
  <div class="bg-gradient-to-br from-[#712bda] to-[#a45deb]">
    <div
      class="px-8 py-7 min-h-screen flex flex-col justify-between md:justify-center items-center w-full md:w-4/12 md:mx-auto"
    >
      <section class="my-auto md:my-10">
        <img
          src="/images/logo.webp"
          width="73"
          height="85"
          alt="Logo"
          class="md:w-44 md:h-auto"
        />
      </section>
      <div class="flex flex-col gap-4 w-full">
        <input
          v-model="title"
          name="title"
          type="text"
          class="py-3 rounded-full flex flex-col text-center placeholder:text-[#64748b]"
          placeholder="Artist / Album / Title"
        />
        <button
          class="py-3 rounded-full text-white bg-white/20 disabled:bg-white/50"
          :disabled="isDisable"
          @click="search"
        >
          Search
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

type IData = {
  title: string | undefined
}

export default Vue.extend({
  name: 'IndexPage',
  data(): IData {
    return {
      title: '',
    }
  },
  computed: {
    isDisable() {
      if (this.title === '') {
        return true
      }

      return false
    },
  },
  methods: {
    search() {
      this.$router.push({
        name: 'result',
        query: {
          title: this.title,
        },
      })
    },
  },
})
</script>
