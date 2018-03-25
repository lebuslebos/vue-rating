<template>
    <div>
        <input type="hidden" name="rate" v-model="rate">
        <small v-text="hintArr[enter]"></small>
        <div>
            <i class="fa fa-star"
               v-for="n in 7"
               :class="{'enter':n<=enter}"
               @mouseenter="onEnter(n)"
               @mouseleave="onLeave()"
               @click="setRate(n)"
            ></i>
            &nbsp;<span :class="{'enter':rate!==0}">{{enter}}</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "rate",
        data() {
            return {
                enter: 0,
                rate: 0,
                hintArr: ['打分必须要填的', '史上第一差', '很差', '比较差', '马马虎虎', '值得一用', '推荐用', '万年回购'],
            }
        },
        methods: {
            onEnter(n) {
                this.enter = n;
                this.hint = this.hintArr[n]
            },
            onLeave() {
                this.enter = this.rate;
            },
            setRate(n) {
                this.rate = n
            },
        }
    }
</script>

<style scoped>
    .fa-star, span {
        font-size: 2rem;
        color: #DADADA;
    }

    .fa-star {
        cursor: pointer;
    }

    .enter {
        color: #FFAA00;
    }
</style>
