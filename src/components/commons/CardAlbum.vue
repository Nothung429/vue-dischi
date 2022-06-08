<template>
    <div class="album">
        <img :src="album.poster" :alt="album.author">
        <h3 class="my-3">{{album.title}}</h3>
        <h5>{{album.author}}</h5>
        <p>{{album.year}}</p>
    </div>
</template>

<script>
    export default {
        name: 'CardCharacter',
        props: {
            album: Object,
        }
    }
</script>

<style lang="scss" scoped>
    .album {
        background-color: #2e3a46;
        text-align: center;
        img {
            max-width: 100%;
        }
        h3 {
            color: #fff;
            font-size: 22px;
        }
        p, h5 {
            font-size: 18px;
            color: lightgreen;
            margin: 0;
        }
    }
</style>