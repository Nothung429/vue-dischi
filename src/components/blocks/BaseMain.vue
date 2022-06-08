<template>
    <main>
        <SectionAlbum/>
    </main>
</template>

<script>
import SectionAlbum from '../sections/SectionAlbum.vue';

    export default {
        name: 'BaseMain',
        components: { 
            SectionAlbum,
        },
    }
</script>

<style lang="scss" scoped>
    main {
        height: 100vh;
        background-color: #1e2d3b;
    }
</style>