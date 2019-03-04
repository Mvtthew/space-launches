<template>
    <div class="home">
        <div class="home-welcome-page">
            <div class="content">
                <div>
                    <h1 class="display-1">
                        Space Launches
                    </h1>
                    <p class="mb-1">
                        Everything you want to know about upcoming space missions!
                    </p>
                    <small>
                        by Mvtthew
                    </small>
                </div>
            </div>
        </div>
        <div class="row my-5">
            <div class="col-lg-12 my-5">
                <h1 class="text-center display-3">
                    Upcoming space missions
                </h1>
            </div>
            <div class="col-lg-4 mb-4" :key="launch.id" v-for="launch in launches">
                <div class="card p-2 launch">
                    <div class="img-header" :style="{'background-image': 'url(' + launch.rocket.imageURL + ')'}">

                    </div>
                    <h3 class="title">
                        {{launch.name}}
                    </h3>
                    <div class="d-flex justify-content-between mt-1">
                        <p class="start-date" data-toggle="tooltip" data-placement="bottom" title="Mission start date">
                            <i class="bx bx-calendar"></i> {{launch.windowstart}}
                        </p>
                        <p class="end-date" data-toggle="tooltip" data-placement="bottom" title="Mission end date">
                            <i class="bx bx-calendar-check"></i> {{launch.windowend}}
                        </p>
                    </div>

                    <hr class="my-2">

                    <p class="mb-0">
                        <i class="bx bxs-map-alt"></i> Launch pad/s
                    </p>

                    <div class="pads mt-2" v-for="(pad, index) in launch.location.pads" :key="pad.id">
                        <a :href="pad.mapURL" target="_blank" class="h6">#{{index + 1}} - {{pad.name}}</a> by<br>
                        <ul class="mb-0">
                            <li v-for="agency in pad.agencies" :key="agency.id">
                                <a :href="agency.infoURL">{{agency.name}}</a> | {{agency.countryCode}}
                            </li>
                        </ul>
                        <a :href="pad.wikiURL" class="d-block text-right mt-2" target="_blank"><i class="bx bxl-wikipedia"></i> More about this launch pad</a>
                    </div>

                    <hr class="my-2">

                    <p class="mb-0">
                        <i class="bx bxs-map"></i> {{launch.location.name}} [{{launch.location.countryCode}}]
                        <a :href="launch.location.infoURL" v-if="launch.location.infoURL !== '' ">About this localization</a>
                    </p>

                </div>

            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'home',
        data() {
            return {
                launches: [],
                launchesAmount: 3,
            }
        },
        created() {
            this.getLaunches();
        }
        ,
        methods: {
            getLaunches() {
                fetch('https://launchlibrary.net/1.3/launch/next/' + this.launchesAmount, {
                    method: 'GET'
                }).then(res => res.json()).then(data => this.launches = data.launches);
            }
        },
    }

</script>

<style lang="scss">

    .home-welcome-page{
        height: calc(100vh - 56px);
        width: calc(100% + 30px);
        position: relative;
        display: flex;
        margin: 0 -15px;
        align-items: center;
        justify-content: center;
        background: url("https://upload.wikimedia.org/wikipedia/commons/6/69/Cygnus_Wall.jpg");
        background-position: left;
        background-size: cover;

        .content{
            z-index: 5;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            background-color: rgba(0, 0, 0, 0.8);
            div{
                text-align: center;
            }
        }
    }
    .launch{
        .img-header{
            height: 26rem;
            background-position: center;
            background-size: 100%;
            background-repeat: no-repeat;
            background-color: black;
            transition: 0.5s all;
            margin-bottom: 0.8rem;
            &:hover{
                background-size: 50%;
            }
        }
        .title{
            font-weight: 300;
        }
        .start-date, .end-date{
            margin: 0;
            font-size: 0.8rem;
        }
        .location{

        }
    }
</style>
