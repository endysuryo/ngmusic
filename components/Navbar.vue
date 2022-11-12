<template>
  <nav
    class="flex flex-row justify-between items-center sticky top-0 bg-gradient-to-r from-[#712bda] to-[#a45deb] w-full p-4 shadow-md z-[998]"
  >
    <img src="/images/menu.webp" width="14" height="auto" alt="menu" />
    <img src="/images/ngmusic.webp" width="72" height="auto" alt="menu" />
    <img
      src="/images/search.webp"
      width="14"
      height="auto"
      alt="menu"
      @click="showModal = !showModal"
    />
    <div v-if="showModal" class="absolute top-0 left-0">
      <figure class="w-screen h-screen bg-black/90">
        <img
          src="/images/close.webp"
          width="18"
          height="auto"
          alt="menu"
          class="absolute top-5 right-3 cursor-pointer"
          @click="showModal = !showModal"
        />
        <div
          class="flex flex-col gap-4 px-8 m-auto w-full h-screen my-auto py-52"
        >
          <h1 class="text-white text-center text-lg font-bold">Search</h1>
          <input
            v-model="title"
            name="title"
            type="text"
            class="py-3 rounded-full flex flex-col text-center placeholder:text-[#64748b]"
            placeholder="Artist / Album / Title"
          />
          <button
            class="py-3 rounded-full text-white bg-gradient-to-br from-[#712bda] to-[#a45deb]disabled:bg-white/50"
            :disabled="isDisable"
            @click="search"
          >
            Search
          </button>
        </div>
      </figure>
    </div>
  </nav>
</template>

<script lang="ts">
type IData = {
  showModal: boolean
  title: string | undefined
}

export default {
  name: 'AppBar',
  data(): IData {
    return {
      showModal: false,
      title: '',
    }
  },
  methods: {
    search() {
      this.$router.push({
        name: 'result',
        query: {
          title: this.title,
        },
      })
      this.showModal = false
    },
  },
}
</script>
