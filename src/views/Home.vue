<template>
    <div class="home">
        <div class="home-welcome-page">
            <div class="content">
                <div>
                    <h1 class="display-1">
                        Space Launches
                    </h1>
                    <p>
                        Everything you want to know about upcoming space missions!
                    </p>
                </div>
            </div>
        </div>
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
    @keyframes transfer-slider {
        0% {
            background-position: left;
        }
        50% {
            background-position: right;
        }
        100% {
            background-position: left;
        }
    }

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
        animation-name: transfer-slider;
        animation-duration: 155s;
        animation-iteration-count: infinite;

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
    }
</style>
