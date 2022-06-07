<template>
    <section>
        <div class="container">
            <div class="row py-5">
                <CardAlbum class="col-6 col-lg-2 p-3" v-for="(album, index) in albums" :key="index" :album="album"/>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import CardAlbum from '../commons/CardAlbum.vue';

    export default {
        name: 'SectionAlbum',
        data () {
            return {
                albums: [],
            }
        },
        components: {
            CardAlbum,
        },
        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.albums = response.data.response;
            })
            .catch((error) => {
                console.log(error);
            });
        }
    }
</script>

<style lang="scss" scoped>
    section {
        background-color: #1e2d3b;
        .container {
            .row {
                justify-content: center;
                gap: 20px;
            }
        }
    }
</style>