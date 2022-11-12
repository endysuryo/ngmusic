<template>
  <div class="bg-[#f8fafc] min-h-screen">
    <NavBar />
    <div class="flex flex-row justify-center items-center gap-4 py-10">
      <div class="text-[#334155]">Search result for :</div>
      <div class="text-[#7b34dd] font-bold text-lg">
        {{ $route.query.title || 'Empty' }}
      </div>
    </div>
    <div
      v-if="$route.query.title.toLowerCase() === 'jason mraz'"
      class="grid overflow-hidden grid-cols-1 auto-rows-max gap-6 md:w-1/2 mx-4 md:mx-auto"
    >
      <section v-for="item in songs" :key="item.id">
        <CardSong
          :id="item.id"
          :genre="item.genre"
          :artist="item.artist"
          :title="item.title"
          :image="item.image"
          :price="item.price"
        />
      </section>
      <button
        class="px-6 py-2 bg-[#e2e8f0] text-[#64748b] mx-auto rounded-full mb-10"
      >
        Load More
      </button>
    </div>
    <div v-else class="text-[#334155] text-center">No data</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import NavBar from '~/components/Navbar.vue'
import CardSong from '~/components/Cardsong.vue'

type ISong = {
  id: number
  artist: string
  title: string
  image: string
  genre: string
  price: string
}

type IData = {
  songs: ISong[]
}

export default Vue.extend({
  name: 'Result',
  components: {
    NavBar,
    CardSong,
  },
  data(): IData {
    return {
      songs: [
        {
          id: 1,
          artist: 'Travie McCoy',
          title: 'Rough Water (feat. Jason Mraz)',
          image: '/images/song_1.jpeg',
          genre: 'Pop',
          price: '1.9',
        },
        {
          id: 2,
          artist: 'Json Mraz',
          title: 'Sleeping to Dream',
          image: '/images/song_2.jpeg',
          genre: 'Pop',
          price: '1.29',
        },
        {
          id: 3,
          artist: 'Json Mraz',
          title: 'Everybodys Got Somebody But Me (feat. Jason Mraz)',
          image: '/images/song_3.jpeg',
          genre: 'Pop',
          price: '1.29',
        },
        {
          id: 4,
          artist: 'Json Mraz',
          title: 'You & I Both',
          image: '/images/song_4.jpeg',
          genre: 'Pop',
          price: '0.29',
        },
      ],
    }
  },
})
</script>
