<template>
    <section>
        <div class="container">
            <div class="row pt-5 px-5">
                <label>Selected: {{ selected }}</label>
                <select v-model="selected">
                    <option disabled value="">All</option>
                    <option>Rock</option>
                    <option>Metal</option>
                    <option>Pop</option>
                    <option>Jazz</option>
                </select>
            </div>
            <div class="row py-5">
                <CardAlbum class="col-6 col-lg-2 p-3" v-for="(album, index) in filterGenre" :key="index" :album="album"/>
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
                selected: "",
            }
        },
        components: {
            CardAlbum,
        },
        computed: {
            filterGenre() {
                return this.albums.filter((elm) => { 
                    return elm.genre.toLowerCase().includes(this.selected.toLowerCase());
                });
            }
        },
        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.albums = response.data.response;
            })
            .catch((error) => {
                console.log(error);
            });
        },
    }
</script>

<style lang="scss" scoped>
    section {
        .container {
            .row {
                justify-content: center;
                gap: 20px;
                label {
                    color: #fff;
                }
            }
        }
    }
</style>