<template>

    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <router-link to="/" class="navbar-brand">Space Launches</router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                    <router-link class="nav-link" to="/">Home <span class="sr-only">(current)</span></router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" to="/about">About</router-link>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="https://github.com/Mvtthew/space-launches" target="_blank">Source code <i class="bx bxl-github" style="color: white !important;"></i></a>
                </li>
            </ul>
        </div>
    </nav>

</template>

<script>
    export default {
        name: 'navbar'
    }
</script>

<style lang="scss" scoped>
    nav{
        position: sticky !important;
        top: 0;
        z-index: 500;

        &.bg-dark{
            background: linear-gradient(40deg, #45145A, #312A6C);
        }
    }
</style>