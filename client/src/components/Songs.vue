<template>

  <v-layout coulmn>
    <v-flex xs6 offset-xs3>
      <panel title="Songs">
        <v-btn class="cyan accent-1"
          slot="action"
          @click="navigateTo({name: 'songs-create'})"
          light
          small
          absolute
          right
          middle
          fab>
          <v-icon>add</v-icon>
        </v-btn>
        <div 
          v-for="song in songs" 
          class="song"
          :key="song.id">

          <v-layout>
            <v-flex xs6>
              <div class="song-title">
                {{song.title}}
              </div>
              <div class="song-artist">
                {{song.artist}}
              </div>
              <div class="song-genre">
                {{song.genre}}
              </div>

              <v-btn
                dark
                class="cyan"
                @click="navigateTo({
                  name: 'song', 
                  params: {
                    songId: song.id
                  }
                })">
                View
              </v-btn>
            </v-flex>
              
            <v-flex xs6>
              <img :src="song.albumImageUrl" alt="" class="album-image" style="width: 300px;"/>
            </v-flex>
          </v-layout>
        </div>

      </panel>
    </v-flex>
  </v-layout>

</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'
export default {
  components: {
    Panel
  },
  data () {
    return {
      songs: null
    }
  },
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  },
  async mounted () {
    //  request backnd for all the songs
    this.songs = (await SongsService.index()).data
  }
}
</script>

<style scoped>

textarea {
    width: 100%;
    font-family: monospace;
    border: none;
    height: 600px;
    border-style: none;
    border-color: transparent;
    overflow: auto;
    padding: 40px;
}

</style>
