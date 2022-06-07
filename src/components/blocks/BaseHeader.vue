<template>
    <header>
        <div class="header__logo">
            <img src="../../assets/img/spotify-logo.png" alt="">
        </div>
    </header>
</template>

<script>
    export default {
        name: 'BaseHeader',
    }
</script>

<style lang="scss" scoped>
    header {
        background-color: #2e3a46;
        height: 80px;
        padding: 0 20px;
        display: flex;
        align-items: center;
        .header__logo {
            height: 70px;
            width: 80px;
            img {
                max-width: 100%;
            }
        }
    }
</style>