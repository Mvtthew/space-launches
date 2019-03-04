<template>
    <div id="app">
        <navbar></navbar>
        <div class="container-fluid">
            <router-view/>
        </div>
    </div>
</template>

<script>

    import Navbar from "./components/Navbar";
    export default {
        components: {Navbar}
    }

</script>

<style lang="scss">
    .bx{
        color: #45145A !important;
        font-weight: 800;
        &.bxl-vuejs, &.bxl-github{
            font-weight: 100;
            color: black !important;
        }
    }
</style>
