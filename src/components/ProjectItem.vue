<template>
    <div class="project-item">
        <a class="my-link" target="_blank" :href="item.link"></a>
        <h3>{{ `0${item.id}  ${item.title}` }}</h3>
        <div class="container">
            <p class="content">{{ item.content }}</p>
            <img v-if="item.imgSrc" :src="require(`../assets/images/${item.imgSrc}.png`)" alt="" />
        </div>
        <span class="time">{{ item.time }}</span>
    </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
};
</script>

<style lang="less" scoped>
.project-item {
    // width: 360px;
    // height: 300px;
    width: 100%;
    min-height: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #000;
    padding: 12px 15px;
    margin-bottom: 30px;
    user-select: none;
    border-radius: 5px;
    position: relative;
    transition: box-shadow 0.3s;
    overflow: hidden;
    &:hover {
        box-shadow: 0 5px 25px #c7c9cb;
    }
    .my-link {
        position: absolute;
        width: 100%;
        height: 100%;
        background: transparent;
        z-index: 2;
        top: 0;
        right: 0;
    }
    h3 {
        width: 100%;
        font-size: 24px;
        margin-bottom: 15px;
        color: #2c405a;
        text-align: left;
    }
    .container {
        width: 100%;
        display: flex;
        align-items: center;
        p {
            margin: 0 15px 12px 0;
            font-size: 18px;
            text-indent: 30px;
            color: #3b4f6a;
        }
        img {
            width: auto;
            height: 80px;
        }
    }
    .time {
        position: absolute;
        right: 22px;
        bottom: 10px;
        opacity: .6;
    }
}
</style>