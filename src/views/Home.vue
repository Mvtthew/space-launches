<template>
    <div class="home">
        <h1>
            This is HOME
        </h1>
        <div class="row">
            <div class="col-lg-12">
                <h1>
                    Upcoming events
                </h1>
            </div>
            <div class="col-lg-4" :key="launch.id" v-for="launch in launches">
                <div class="card p-2 launch">
                    <div class="img-header" :style="{'background-image': 'url(' + launch.rocket.imageURL + ')'}">

                    </div>
                    <h3 class="title">
                        {{launch.name}}
                    </h3>
                    <div class="d-flex justify-content-between">
                        <p class="start-date" data-toggle="tooltip" data-placement="bottom" title="Mission start date">
                            <i class="bx bx-calendar"></i> {{launch.windowstart}}
                        </p>
                        <p class="end-date" data-toggle="tooltip" data-placement="bottom" title="Mission end date">
                            <i class="bx bx-calendar-check"></i> {{launch.windowend}}
                        </p>
                    </div>

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
    .launch{
        .img-header{
            height: 26rem;
            background-position: center;
            background-size: 100%;
            background-repeat: no-repeat;
            background-color: black;
            transition: 0.5s all;
            &:hover{
                background-size: 65%;
            }
        }
        .title{

        }
        .start-date, .end-date{
            margin: 0;
            font-size: 0.8rem;
        }
    }
</style>
