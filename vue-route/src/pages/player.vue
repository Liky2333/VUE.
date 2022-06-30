<template>
    <div class="page">
        <!-- 播放器 -->
        <div class="player" ref="playerContain">
            <div class="tools">
                <i class="left fa fa-chevron-left" @click="onGoHome"></i>
                <i class="right fa fa-upload"></i>
            </div>
            <div class="video">
                <!-- <video src="../assets/video/video.mp4" controls></video> -->
                <video src="../assets/video/funny.mp4" ref="player" @click.stop="onPlay"></video>
                <div class="btn" v-show="isPause" @click.stop="onPlay">
                    <i
                        :class="['play fa', isPause ? 'fa-play-circle' : 'fa-pause-circle']"
                        
                    ></i>
                </div>
            </div>
        </div>
        <div class="content-box" :style="{ marginTop: vidHeight + 'px' }">
            <div class="content">
                <!-- 电影内容 -->

                <div class="movie-card">
                    <div class="body">
                        <h3 class="name">搞笑影片</h3>
                        <p class="info">片中职务：导演/编剧</p>
                    </div>
                    <div class="icon">
                        <i class="fa fa-angle-right detail"></i>
                    </div>
                </div>

                <!-- 推荐列表 -->
                <div class="interest">
                    <template v-for="cate in interestData" :key="cate.name">
                        <h3 class="title">{{ cate.name }}</h3>
                        <div class="list-row">
                            <div class="list" :style="{ width: (200 + 5) * cate.data.length + 'px' }">
                                <!-- 电影列表 -->
                                <div
                                    v-for="mv in cate.data"
                                    class="category-card"
                                    :style="{ backgroundImage: 'url(' + mv.url + ')' }"
                                >
                                    <div class="info">
                                        <span>{{ cate.name }}</span>/
                                        <span>{{ mv.length }} / {{ (200 + 5) * cate.data.length }}</span>
                                    </div>
                                    <div class="name">
                                        <span>{{ mv.name }}</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </template>

                    <div></div>
                </div>
            </div>
        </div>

        <div class="msg-box">
            <div class="input-box">
                <label class="fa fa-pencil-square-o"></label>
                <input type="text" />
            </div>
            <div>
                <div class="fa fa-heart-o"></div>
                <div class="count">22</div>
            </div>
            <div>
                <div class="fa fa-upload"></div>
                <div class="count">11</div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    components: {


    },

    data() {
        return {
            isPause: true,
            vidHeight: 0,

            interestData: [
                {
                    name: "励志",
                    data: [
                        { id: 1, name: "电影标题1", url: 'src/assets/img/爱情.jpeg', categ: "类型", length: `2'43"` },
                        { id: 2, name: "电影标题2", url: 'src/assets/img/创意.jpeg', categ: "类型", length: `2'43"` },
                        { id: 3, name: "电影标题3", url: 'src/assets/img/动画.jpeg', categ: "类型", length: `2'43"` },
                        { id: 4, name: "电影标题4", url: 'src/assets/img/搞笑.jpeg', categ: "类型", length: `2'43"` },
                        { id: 5, name: "电影标题5", url: 'src/assets/img/广告.jpeg', categ: "类型", length: `2'43"` },
                    ]
                },
                {
                    name: "温暖",
                    data: [
                        { id: 1, name: "电影标题1", url: 'src/assets/img/混剪.jpeg', categ: "类型", length: `2'43"` },
                        { id: 2, name: "电影标题2", url: 'src/assets/img/纪录.jpeg', categ: "类型", length: `2'43"` },
                        { id: 3, name: "电影标题3", url: 'src/assets/img/剧情.jpeg', categ: "类型", length: `2'43"` },
                        { id: 4, name: "电影标题4", url: 'src/assets/img/科幻.jpeg', categ: "类型", length: `2'43"` },
                        { id: 5, name: "电影标题5", url: 'src/assets/img/励志.jpeg', categ: "类型", length: `2'43"` },
                    ]
                },
                {
                    name: "广告",
                    data: [
                        { id: 1, name: "电影标题1", url: 'src/assets/img/旅行.jpeg', categ: "类型", length: `2'43"` },
                        { id: 2, name: "电影标题2", url: 'src/assets/img/美食.jpeg', categ: "类型", length: `2'43"` },
                        { id: 3, name: "电影标题3", url: 'src/assets/img/汽车.jpeg', categ: "类型", length: `2'43"` },
                        { id: 4, name: "电影标题4", url: 'src/assets/img/生活.jpeg', categ: "类型", length: `2'43"` },
                        { id: 5, name: "电影标题5", url: 'src/assets/img/时尚.jpeg', categ: "类型", length: `2'43"` },
                    ]
                },
            ]
        }
    },


    mounted() {
        // 窗口大小改变，改变内容的 上边距，
        window.addEventListener("resize", (e) => {
            this.onChangeSize()
        })
    },
    updated() {

    },
    methods: {
        onChangeSize() {
            const player = this.$refs["player"];
            this.vidHeight = player.clientHeight

        },
        onPlay() {
            const player = this.$refs["player"];
            // console.log("play/pause", player)

            if (player.paused) {
                player.play()
                this.isPause = false
            } else {
                player.pause()
                this.isPause = true
            }
        },

        // 返回主页
        onGoHome(){
            this.$router.push({
                path: "/"
            })
        }
    },
}
</script>

<style lang="scss">
.page {
    // height: 100vh;
    // overflow: hidden;
    // 播放器
    .player {
        width: 100%;
        position: fixed;
        top: 0;
        z-index: 1;

        .tools {
            width: 100%;
            position: absolute;
            // background-color: rgba(255, 255, 255, 0.274);
            background: transparent;
            top: 0;
            z-index: 1;
            // line-height: 20px;
            i {
                text-shadow: 2px 1px 7px grey;

                color: rgba(255, 255, 255, 0.438);
                padding: 15px;
                font-size: 22px;
                &:hover{
                    color: white;
                }
            }
            .left {
                float: left;
            }
            .right {
                float: right;
            }

        }

        .video {
            // width: 100%;
            height: 100%;
            position: relative;
            video {
                width: 100%;
                max-height: 200px;
                background: black;
            }

            .btn {
                display: flex;
                position: absolute;
                width: 100%;
                height: 100%;
                top: 0;
                align-content: center;
                justify-content: center;
                flex-direction: row;
                flex-wrap: wrap;

                .play {
                    // padding: 20px;
                    border-radius: 50%;
                    display: block;
                    color: rgb(255, 255, 255);
                    font-size: 68px;
                    opacity: 0.6;
                }
                :hover .play {
                    opacity: 0.5;
                }
            }
             &:hover {
                .btn .play {
                    opacity: 1;
                }
            }
        }

       
    }

    .content-box {
        // height: 60%;
        margin-bottom: 50px;
        // 内容
        .content {
            overflow: hidden;
            padding: 0 10px;
            .movie-card {
                padding: 5px 16px;
                position: relative;
                margin: 5px 5px;
                border-bottom: 1px solid #f4f4f4;

                .body {
                    text-align: left;
                }
                .icon {
                    top: 44%;
                    position: absolute;
                    right: 15px;
                }
                i.detail {
                    // color:red;
                    font-size: 22px;
                }
            }

            .interest {
                text-align: left;
                .title {
                }
                .list-row {
                    width: 100%;
                    overflow-y: hidden;
                    overflow-x: scroll;
                    .list {
                        display: flex;
                        // width: 300%;
                        .category-card {
                            display: flex;
                            flex-direction: column;
                            align-items: flex-start;
                            justify-content: flex-end;
                            // border: 1px solid red;
                            background-color: rgb(0, 0, 0);
                            height: 100px;
                            width: 200px;
                            margin-right: 5px;
                            padding-left: 10px;
                            padding-bottom: 10px;
                            box-sizing: border-box;
                            background-size: cover;
                            color: white;
                            .info {
                                font-size: 14px;
                            }
                            .name {
                                font-size: 16px;
                            }
                        }
                    }
                }
            }
        }

    }


    // 聊天栏
    .msg-box {
        display: flex;
        justify-content: space-around;
        font-size: 14px;
        box-shadow: 3px 5px 20px #a6a6a6;
        position: fixed;
        bottom: 0;
        width: 100%;
        padding: 10px 0px;
        background-color: white;
        .input-box {
            display: flex;
            flex-direction: row;
            align-items: center;
            border: 1px solid gray;
            border-radius: 18px;
            padding: 0px 15px;
            font-size: 18px;
            height: 28px;
            input{
                border: none;
                font-size: 18px;
                padding-left: 5px;
                &:focus-visible{
                    outline: none;
                }
            }
        }
    }
}
</style>