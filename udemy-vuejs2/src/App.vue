<template>
    <div class="main">
        <button @click="myAnimation = 'slide'">Slide</button>
        <button @click="myAnimation = 'fade'">Fade</button>
        <p>{{myAnimation}}</p>

        <button @click="show = !show">きりかえ</button>
        <transition
            enter-active-class="animate__animated animate__bounce"
            leave-active-class="animate__animated animate__shakeX"
            appear
        >
            <p v-if="show">hello</p>
        </transition>
        <transition
            name="fade"
            mode="out-in"
        >
            <p v-if="show" key="hi">こんにちは</p>
            <p v-else key="gn">こんばんわ</p>
        </transition>
        <transition
            :name="myAnimation"
            appear
        >
            <div v-if="show" style="background-color: #f4f4f4;">
                <p>bye</p>
                <p>hello</p>
                <p>hello</p>
                <p>hello</p>
                <p>hello</p>
                <p>hello</p>
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    data() {
        return {
            show: true,
            myAnimation: 'slide',
        };
    }
};
</script>

<style scoped>
.fade-enter-from {
    /* 現れる時の最初の状態 */
    opacity: 0;
}
.fade-enter-active {
    /* 現れる時のトランジション状態 */
    transition: opacity 0.5s ease;
}
.fade-enter-to {
    /* 消える時のトランジション状態 */
    opacity: 1;
}
.fade-leave-from {
    /* 消える時の最初の状態 */
    opacity: 1;
}
.fade-leave-active {
    /* 消える時のトランジションの状態 */
    transition: opacity 0.5s ease;
}
.fade-leave-to {
    /* 消える時の最後の状態 */
    opacity: 0;
}

.slide-enter-from {
    opacity: 0;
}
.slide-enter-active {
    animation: slide-in 0.5s;
    transition: opacity 0.5s ease;
}
.slide-enter-to {
    opacity: 1;
}
.slide-leave-from {
    opacity: 1;
}
.slide-leave-active {
    animation: slide-in 0.5s reverse;
    transition: opacity 1s ease;
}
.slide-leave-to {
    opacity: 0;
}

@keyframes slide-in {
    from {
        transform: translateX(100px)
    }
    to {
        transform: translateX(0);
    }
}

.main {
    width: 70%;
    margin: auto;
    padding-top: 5rem;
    text-align: center;
}
</style>