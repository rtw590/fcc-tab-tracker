<template>
    <div>
        <v-layout>
            <v-flex xs6>
                <song-metadata :song="song" />
            </v-flex>

            <v-flex xs6 class="ml-2">
                <you-tube :youtubeId="song.youtubeId" />
            </v-flex>
        </v-layout>
                
                <!-- <v-flex xs6>
                <img :src="song.albumImageUrl" alt="" class="album-image" />
                <br>
                song.album
                </v-flex>
            </v-layout>
                </panel>
            </v-flex>
            <v-flex xs6>
                <panel title="Tabs" class="ml-2">
                    <textarea
                        readonly
                        v-model="song.tab"
                    ></textarea>
                </panel>
            </v-flex>
        </v-layout>
        
        <v-layout>
            <v-flex xs6>
                <panel title="Youtube Video">
                
                </panel>
            </v-flex>
            </v-layout>

        <v-layout>
            <v-flex xs6>
                <panel title="Lyrics" class="ml-2">
                    <textarea
                        readonly
                        v-model="song.lyrics"
                    ></textarea>
                </panel>
            </v-flex>
        </v-layout> -->
    </div>
</template>

<script>
import SongMetadata from './SongMetadata'
import YouTube from './YouTube'
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'

export default {
    data () {
        return {
            song: {}
        }
    },
    async mounted () {
        const songId = this.$store.state.route.params.songId
        this.song = (await SongsService.show(songId)).data
    },
    components: {
        Panel,
        SongMetadata,
        YouTube
    }
}
</script>

<style scoped>

.song {
  padding: 20px;
  height: 330px;
  overflow: hidden;
}

.song-title {
  font-size: 30px
}

.song-artist {
  font-size: 24px
}

.song-genre {
  font-size: 18px
}

.album-image {
  width: 70%;
  margin: 0 auto;
}

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
