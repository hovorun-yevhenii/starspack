<template>
    <div class="rate">
        <p class="paragraph">{{ label }}</p>

        <div @mousemove="mouseMove"
             @mouseout="mouseOut"
             @click="selectRating"
             class="rate__stars-group">
            <rate-star v-for="index in Number(max)"
                       :key="index"
                       :value="index"
                       :rating="rating"
                       :stars_count="max"
                       :clr_prime="clr_prime"
                       :clr_second="clr_second"
                       class="rate__star">
            </rate-star>
        </div>
    </div>
</template>

<script>
    import RateStar from './RateStar'

    export default {
        name: "AppRate",
        components: {
            RateStar
        },
        props: {
            max: {
                default: 5,
                type: Number
            },
            clr_prime: {
                type: String,
                default: "#EBB82F"
            },
            clr_second: {
                type: String,
                default: "#E3E3E3"
            },
            label: String,
            refer: String
        },
        data() {
            return {
                rating: 0,
                selected: 0
            };
        },
        methods: {
            mouseMove({ offsetX, target }) {
                offsetX = offsetX < 16 ? 0 : offsetX;
                // 16px - left padding enables discard selected rating
                this.rating = Math.ceil(offsetX * this.max / target.clientWidth);
            },
            mouseOut() {
                this.rating = this.selected;
            },
            selectRating() {
                this.selected = this.rating;

                this.$emit("change", {
                    refer: this.refer,
                    value: this.rating,
                    max: this.max,
                    percentage: Math.round(100 * this.rating / this.max)
                });
            }
        }
    }
</script>

<style lang="scss" scoped>
    .rate {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        margin-top: 32px;

        & + & {
            margin-top: 44px;
        }

        &__stars-group {
            display: flex;
            align-items: center;
            width: 300px;
            padding: 0 16px;
            cursor: pointer;
        }
    }


    @media (max-width: 768px) {
        .rate {
            & + & {
                margin-top: 24px;
            }
        }
    }

    @media (max-width: 480px) {
        .rate {
            & + & {
                margin-top: 16px;
            }

            &__stars-group {
                width: 220px;
            }
        }
    }
</style>
