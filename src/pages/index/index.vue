<template>
    <div class="home">
        <div class="wrap"></div>
        <div class="cover" :style="coverStyleStr"></div>
        <div class="main">
            <div :style="navBarStyleStr"></div>
            <p class="name">
                {{song ? song.name : ""}}
            </p>
            <p class="artist">
                -&nbsp;{{song ? song.artists[0].name : ""}}&nbsp;-
            </p>
            <swiper class="swiper" :indicator-dots="true" indicator-active-color="rgba(255, 255, 255, .7)">
                <swiper-item>
                    <album></album>
                </swiper-item>
                <swiper-item>
                    <lyric></lyric>
                </swiper-item>
            </swiper>
            <slider block-size="12"
                    activeColor="#2d8cf0"
                    class="slider"
                    @change="sliderChange"
                    :value="progress"
                    id="slider"
                    :style="sliderStyleStr"
                    :disabled="!duration"
                    backgroundColor="rgba(255, 255, 255, .4)"
            />
            <div class="footer">
                <div class="control">
                    <i :class="cycleClassStr" @click="toggleCircle"></i>
                    <i class="iconfont sub icon-last" @click="last"></i>
                    <i :class="playPauseClassStr" @click="playPause"></i>
                    <i class="iconfont sub icon-next" @click="next"></i>
                    <i class="iconfont third icon-collect" @click="collect"></i>
                </div>
                <div class="tab-bar">
                    <i class="iconfont icon-discover third" @click="routeTo('../discover/main')"></i>
                    <i class="iconfont icon-search third"></i>
                    <i class="iconfont icon-user third"></i>
                </div>
            </div>
        </div>
    </div>
</template>

<script src="./index.js"></script>

<style lang="scss" scoped>
    .home {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        color: white;
        .wrap,
        .cover,
        .main {
            position: absolute;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
        }
        .wrap {
            z-index: 4;
            background-color: rgba(0, 0, 0, .8);
        }
        .cover {
            z-index: 5;
            background-repeat: no-repeat;
            background-position: center;
            background-size: cover;
            filter: blur(35px);
            opacity: .5;
        }
        .main {
            display: flex;
            flex-direction: column;
            width: 100%;
            height: 100%;
            z-index: 6;
            .top {
                display: flex;
                width: 100%;
                height: 8vw;
                position: relative;
                span {
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex: 1;
                    &:not(.active) {
                        opacity: .6;
                    }
                }
                .divider {
                    width: 1px;
                    height: 5vw;
                    position: absolute;
                    left: 50%;
                    top: 0;
                    bottom: 0;
                    margin: auto;
                    background: #999;
                }
            }
            .name {
                $height: 10vw;
                text-align: center;
                height: $height;
                line-height: $height;
                font-size: 5.2vw;
            }
            .artist {
                text-align: center;
                font-size: 4vw;
                color: rgba(255, 255, 255, .7)
            }
            .swiper {
                flex: 1;
            }
            .slider {
                margin: 0;
            }
            .footer {
                display:flex;
                flex-direction:column;
                justify-content:space-between;
                box-sizing:border-box;
                padding: 2vw 0 3vw;
                height: 36vw;
                .control,
                .tab-bar {
                    display: flex;
                    flex-wrap: wrap;
                    justify-content: space-around;
                    align-items: center;
                }
                .control {
                    width: 100%;
                    .iconfont {
                        color: rgba(255, 255, 255, .8);
                    }
                    .playPause {
                        font-size: 18vw;
                    }
                }
                .tab-bar {
                }
                .sub {
                    font-size: 11vw;
                }
                .third {
                    font-size: 8vw;
                    color: rgba(255, 255, 255, .7);
                }
                .tab-bar {
                    width: 100%;
                }
            }
        }
    }
</style>
