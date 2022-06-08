<template>
    <section>
        <div class="container">
            <div class="row my-4">
                <div class="genre-selector">
                    <label class="mb-2">Genre selected: {{selected}}</label>
                    <select v-model="selected">
                        <option disabled value="">--select a genre--</option>
                        <option>Rock</option>
                        <option>Metal</option>
                        <option>Pop</option>
                        <option>Jazz</option>
                    </select>
                </div>
            </div>
            <div class="row mb-4">
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
        created() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.albums = response.data.response;
            })
            .catch((error) => {
                console.log(error);
            });
        },
        computed: {
            filterGenre() {
                return this.albums.filter((elm) => { 
                    return elm.genre.toLowerCase().includes(this.selected.toLowerCase());
                });
            }
        },
    }
</script>

<style lang="scss" scoped>
    section {
        .container {
            .row {
                justify-content: center;
                gap: 20px;
                .genre-selector {
                    display: flex;
                    flex-direction: column;
                    width: 450px;
                    label {
                        font-size: 20px;
                        color: #fff;
                    }
                    select {
                        background-color: #2e3a46;
                        color: #fff;
                        border-radius: 10px;
                        padding: 5px 8px;
                    }
                }
            }
        }
    }
</style>