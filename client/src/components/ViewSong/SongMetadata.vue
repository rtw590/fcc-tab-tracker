<template>
    <panel title="Song Metadata">
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
            </v-flex>
            
            <v-flex xs6>
                <img :src="song.albumImageUrl" alt="" class="album-image" />
                <br>
                {{song.album}}
            </v-flex>
        </v-layout>
    </panel>
</template>

<script>
export default {
}
</script>

<style scoped>

</style>
