<template>
    <div class="project-home">
        <div class="me">
            <h1>HI, MY NAME IS <span>CHENG</span></h1>
            <p>I want to be a better web developer</p>
            <div class="my-img">
                <img src="../assets/images/my.jpg" alt="" />
                <svg @click="skip" class="icon my-icon" aria-hidden="true">
                    <use xlink:href="#icon-xiangji"></use>
                </svg>
                <!-- <i class="iconfont icon-xiangji my-icon" @click="skip"></i> -->
            </div>
        </div>
        <section id="section-one" ref="section">
            <div class="left" ref="left">
                <div class="show-text">
                    <h3>我的项目</h3>
                    <p>
                        学习前端以来，自己做的一些项目，也算是对自己学习能力的考验。但这些我并不认为它是我学习的成果，而是我成长的历程。。。
                    </p>
                </div>
                <button @click="open(1)">TOUCH</button>
            </div>
            <div class="mid" ref="mid">
                <div v-if="flag === 1">
                    <h3 class="title">我的项目</h3>
                    <div class="list-all">
                        <ProjectItem
                            v-for="item in projectIntr"
                            :key="item.id"
                            :item="item"
                        />
                    </div>
                </div>
                <div v-else>
                    <h3>关于我</h3>
                    <div class="about-con">
                        <ul class="about-text">
                            <li>热爱旅行，热爱技术；</li>
                            <li>目标坐标杭州；</li>
                            <li>
                                博客里是我日常学习的一些总结，若有不足，欢迎指正。
                            </li>
                        </ul>
                        <ul class="about-list">
                            <li>
                                <span class="git"
                                    ><i
                                        class="iconfont icon-github about-icon"
                                    ></i>
                                    <span>GitHub：</span>
                                    <a
                                        href="https://github.com/bcdxc"
                                        target="_blank"
                                        >@bcdxc</a
                                    >
                                </span>
                            </li>
                            <li>
                                <span class="git"
                                    ><i
                                        class="iconfont icon-biji about-icon"
                                    ></i>
                                    <span>博 &nbsp; 客：</span>
                                    <a
                                        href="https://www.yuque.com/u12065467"
                                        target="_blank"
                                        >@ysgs</a
                                    >
                                </span>
                            </li>
                        </ul>
                        <div class="about-bottom">
                            <img src="../assets/images/love.png" alt="" />
                            <p>不勤于始，将悔于终</p>
                        </div>
                    </div>
                </div>
                <i class="icon-guanbi iconfont close" @click="close"></i>
            </div>
            <div class="right" ref="right">
                <div class="show-text">
                    <h3>关于我</h3>
                    <p class="come-on">加油 &nbsp; 💪</p>
                </div>
                <button @click="open(2)">TOUCH</button>
            </div>
            <div class="mask" ref="mask"></div>
        </section>
    </div>
</template>

<script>
import ProjectItem from "./ProjectItem.vue";
export default {
    components: {
        ProjectItem,
    },
    data() {
        return {
            projectIntr: [
                {
                    id: 1,
                    title: "Conlate",
                    content:
                        "使用 BootStrap 栅格系统进行排版布局，使用 Swiper 和 animate 插件分别制作轮播图和动画效果，采用 JQuery 编写交互效果。",
                    link: "https://bcdxc.github.io/Conlate/",
                    imgSrc: "conlate",
                },
                {
                    id: 2,
                    title: "GP",
                    content:
                        "效仿和平精英官网制作，Flex 弹性盒子布局，JavaScript 原生编写交互效果。",
                    link: "https://bcdxc.github.io/MyPUBG/",
                    imgSrc: "gp",
                },
                {
                    id: 3,
                    title: "Aruk",
                    content:
                        "使用 Swiper 和 animate 插件分别制作轮播图和动画效果，代码使用 JQuery 和 原生 JavaScript 编写。",
                    link: "https://bcdxc.github.io/MyAruk/",
                    imgSrc: "aruk",
                },
                {
                    id: 4,
                    title: "Albatross",
                    content:
                        "一个 JavaScript 论坛项目，使用 Vue 框架以及 vue-router 和 vuex 制作，axios 请求数据，使用 ElementUI 库。",
                    link: "https://bcdxc.github.io/Albatross/#/",
                    imgSrc: "albatross",
                },
                {
                    id: 5,
                    title: "Yiguo",
                    content:
                        "一个微信小程序项目，使用 iView 组件库，原生小程序框架编写，管理平台使用 Vue 框架与 ElementUI 组件库，axios 请求数据。",
                    link: "https://github.com/bcdxc/yiguo",
                    imgSrc: "yiguo",
                },
            ],
            flag: 1,
        };
    },
    methods: {
        open(target) {
            this.flag = target;
            // document.body.scrollHeight   --->  整个文档的高度
            // document.documentElement.clientHeight  --->  浏览器的高度
            // document.documentElement.scrollTop  --->  滚动条距离顶部的距离
            // 文档本身的高度 - 浏览器的高度 - 滚动条距离顶部的距离 = 滚动条距离浏览器底部的距离
            this.scrollTo(this.changeDomClass);
        },

        changeDomClass() {
            const mid = this.$refs.mid;
            const left = this.$refs.left;
            const right = this.$refs.right;
            const mask = this.$refs.mask;
            const midDiv = mid.firstChild;
            if (arguments.length) {
                left.classList.remove("left-transform");
                right.classList.remove("right-transform");
                mask.classList.remove("mask-display");
                mid.classList.remove("mid-transform");
                midDiv.classList.remove("mid-content");
                document.body.classList.remove("body-overflow");
                return;
            }
            left.classList.add("left-transform");
            right.classList.add("right-transform");
            mask.classList.add("mask-display");
            mid.classList.add("mid-transform");
            midDiv.classList.add("mid-content");
            document.body.classList.add("body-overflow");
        },

        scrollTo(callback) {
            // 获取页面到底部的距离，如果为 0 就调用函数；
            const documentHeight = document.body.scrollHeight;
            const browserHeight = document.documentElement.clientHeight;

            const onScroll = function () {
                const scrollFromTop = document.documentElement.scrollTop;
                const scrollBottom =
                    documentHeight - browserHeight - scrollFromTop;
                const scrollFromBottom =
                    Math.floor(scrollBottom) > 0 ? Math.floor(scrollBottom) : 0;
                if (scrollFromBottom === 0) {
                    window.removeEventListener("scroll", onScroll);
                    callback();
                }
            };
            window.addEventListener("scroll", onScroll);
            onScroll();
            window.scrollTo({
                top: documentHeight,
                behavior: "smooth",
            });
        },

        close() {
            this.changeDomClass(1);
        },

        skip() {
            this.open(2);
        },
    },
};
</script>

<style lang="less" scoped>
.me {
    background-image: linear-gradient(to bottom right, #fc00ff, #00dbde);
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    h1 {
        color: #fff;
        font-size: 76px;
        font-weight: 400;
        margin-top: 120px;
        span {
            background-image: linear-gradient(
                to bottom right,
                #00d2ff,
                #b4eaee
            );
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    }
    p {
        font-size: 30px;
        color: #fff;
        letter-spacing: 1.4px;
        margin: 30px 0 100px;
    }
    .my-img {
        width: 220px;
        height: 147px;
        position: relative;
        &:hover::before {
            opacity: 0.8;
        }
        &:hover .my-icon {
            opacity: 1;
        }
        &::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background-image: linear-gradient(
                to bottom right,
                #12c2e9,
                #c471ed,
                #f64f59
            );
            opacity: 0;
            border-radius: 5px;
            transition: opacity 0.6s;
        }
        img {
            width: 100%;
            border-radius: 6px;
        }
        .my-icon {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 30px;
            height: 30px;
            cursor: pointer;
            opacity: 0;
            transition: opacity 0.6s;
        }
    }
}

/* section-one */
#section-one {
    width: 100%;
    height: 100vh;
    display: flex;
    overflow: hidden;
    position: relative;
    .left {
        background-image: linear-gradient(to bottom right, #c883ed, #ff8888);
    }
    .right {
        background-image: linear-gradient(to bottom right, #16bffd, #cb3066);
    }
    .left,
    .right {
        width: 50%;
        padding: 50px;
        display: flex;
        flex-direction: column;
        align-items: center;
        color: #fff;
        transition: transform 0.6s;
        &:hover .show-text {
            transform: translateY(-40px);
        }
        &:hover button {
            transform: translateY(-40px);
            opacity: 1;
        }
        .show-text {
            margin-top: 140px;
            display: flex;
            flex-direction: column;
            align-items: center;
            transform: translateY(40px);
            transition: transform 0.8s;
            .come-on {
                text-indent: 0;
                text-align: center;
            }
        }
        h3 {
            font-size: 30px;
            letter-spacing: 1.8px;
        }
        p {
            width: 400px;
            margin: 20px 0 30px;
            text-indent: 34px;
            font-size: 18px;
            color: #ece7e7;
        }
        button {
            outline: 0;
            width: 130px;
            height: 50px;
            border-radius: 28px;
            border: 1px solid rgba(255, 255, 255, 0.7);
            cursor: pointer;
            background: transparent;
            color: rgba(255, 255, 255, 0.6);
            font-size: 18px;
            transition: all 0.8s;
            transform: translateY(40px);
            opacity: 0;
            &:hover {
                color: rgba(255, 255, 255, 1);
                border-color: rgba(255, 255, 255, 1);
            }
        }
    }
    .left-transform {
        transform: translateX(-50%);
    }
    .right-transform {
        transform: translateX(50%);
    }
    .mid {
        width: 60%;
        height: 100%;
        min-height: 100vh;
        overflow: scroll;
        position: absolute;
        top: 0;
        left: 50%;
        margin-left: -30%;
        z-index: 100;
        color: #000;
        background-color: #f5f3f3;
        padding: 16px;
        display: flex;
        flex-direction: column;
        align-items: center;
        transform-origin: center center;
        transform: scaleX(0);
        transition: transform 0.6s;
        & > div {
            opacity: 0;
            transform: translateY(-100px);
            transition: all 0.6s;
            width: 100%;
        }
        &::-webkit-scrollbar {
            width: 5px;
            height: 0;
            background-color: #f5f5f5;
        }
        /*定义滚动条轨道 内阴影+圆角*/
        &::-webkit-scrollbar-track {
            box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            background-color: #f5f5f5;
        }
        /*定义滑块 内阴影+圆角*/
        &::-webkit-scrollbar-thumb {
            border-radius: 10px;
            box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
            background-color: #bdbdbd;
        }
        /*滑块效果*/
        &::-webkit-scrollbar-thumb:hover {
            border-radius: 5px;
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
            background: rgba(0, 0, 0, 0.4);
        }
        &::-webkit-scrollbar-button {
            width: 0px;
        }
        h3 {
            font-size: 26px;
            color: #2c405a;
            margin-bottom: 30px;
            text-align: center;
            letter-spacing: 3px;
        }
        .list-all {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
        .about-con {
            width: 100%;
            padding: 0 100px;
            color: #3b4f6a;
            margin-top: 20px;
            position: relative;
            .about-text {
                font-size: 18px;
                margin-bottom: 30px;
                li {
                    margin-bottom: 6px;
                }
            }
            .about-list li {
                font-size: 18px;
                margin-bottom: 12px;
                a {
                    color: #6747a7;
                    transition: color 0.4s;
                    &:hover {
                        color: #4d3087;
                    }
                }
                .git {
                    span {
                        display: inline-block;
                        width: 80px;
                        text-align: center;
                    }
                    .about-icon {
                        font-size: 18px;
                    }
                    i {
                        margin-right: 5px;
                    }
                }
            }
            .about-bottom {
                position: absolute;
                left: 50%;
                bottom: -350px;
                transform: translateX(-50%);
                img {
                    width: 200px;
                    height: auto;
                    border-radius: 50%;
                    margin-bottom: 30px;
                }
                p {
                    text-align: center;
                    font-size: 18px;
                }
            }
        }
        .close {
            position: absolute;
            top: 20px;
            right: 25px;
            width: 30px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            color: #2c405a;
            font-size: 20px;
            cursor: pointer;
        }
        & > .mid-content {
            opacity: 1;
            transform: translateY(0);
        }
    }
    .mid-transform {
        transform: scaleX(1);
    }
    .mask {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        z-index: 99;
        background-color: rgba(28, 23, 38, 0.6);
        display: none;
    }
    .mask-display {
        display: block;
    }
}
</style>