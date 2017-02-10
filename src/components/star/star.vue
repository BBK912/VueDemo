<template lang="html">
    <div class="star" :class="starType">
        <span v-for="itemClasses in itemClasses"
              :class="itemClasses" class="star-item" track-by="$index"></span>
    </div>
</template>

<script>
    const STAR_LEN = 5
    const CLS_ON = 'on'
    const CLS_HALF = 'half'
    const CLS_OFF = 'off'
    export default {
        props: {
            size: {
                type: Number
            },
            score: {
                type: Number
            }
        },
        computed: {
            starType () {
                return 'star-' + this.size
            },
            itemClasses () {
                let result = []
                let score = Math.floor(this.score * 2) / 2
                let hasDecimal = score % 1 !== 0
                let interger = Math.floor(score)
                for (let i = 0; i < interger; i++) {
                    result.push(CLS_ON)
                }
                if (hasDecimal) {
                    result.push(CLS_HALF)
                }
                while (result.length < STAR_LEN) {
                    result.push(CLS_OFF)
                }
                return result
            }
        }
    }
</script>

<style lang="scss" rel="stylesheet/scss">
    @import "../../common/sass/mixin.scss";
    .star {
        font-size: 0;
        .star-item {
            display: inline-block;
            background-repeat: no-repeat;
        }
        &.star-48 {
            .star-item {
                width: 20px;
                height: 20px;
                margin-right: 22px;
                background-size: 20px 20px;
                &.on {
                    @include bg-img('star48_on');
                }
                &.half {
                    @include bg-img('star48_half');
                }
                &.off {
                    @include bg-img('star48_off');
                }
                &:last-child {
                    margin-right: 0;
                }
            }
        }
        &.star-36 {
            .star-item {
                width: 15px;
                height: 15px;
                margin-right: 6px;
                background-size: 15px 15px;
                &.on {
                    @include bg-img('star36_on');
                }
                &.half {
                    @include bg-img('star36_half');
                }
                &.off {
                    @include bg-img('star36_off');
                }
                &:last-child {
                    margin-right: 0;
                }
            }
        }
        &.star-24 {
            .star-item {
                width: 10px;
                height: 10px;
                margin-right: 3px;
                background-size: 10px 10px;
                &.on {
                    @include bg-img('star24_on');
                }
                &.half {
                    @include bg-img('star24_half');
                }
                &.off {
                    @include bg-img('star24_off');
                }
                &:last-child {
                    margin-right: 0;
                }
            }
        }

    }
</style>
