<template>
    <svg viewBox="0 0 40 38" :width="starWidth" class="star">
        <path :fill="starColor" d="M20.791.574l5.663 11.328 12.663 1.816c.763.11 1.068 1.035.516 1.566l-9.163
            8.817 2.163 12.45c.13.75-.667 1.322-1.35.968l-11.326-5.878-11.326 5.878c-.682.354-1.48-.218-1.35-.968
            l2.164-12.45-9.163-8.817c-.552-.531-.247-1.457.515-1.566l12.663-1.816L19.123.574
            c.341-.682 1.327-.682 1.668 0"></path>
        <path fill="rgba(255,255,255,.5)" d="M3.427 15.697a.463.463 0 0 1-.46-.393.46.46 0 0 1 .393-.52
            l11.027-1.582 4.978-9.957a.467.467 0 0 1 .622-.209c.23.112.326.387.212.615l-5.087 10.173
            a.464.464 0 0 1-.35.251L3.494 15.692a.425.425 0 0 1-.067.005M9.494 35.18a.46.46 0 0 1-.459-.537
            l1.539-8.852a.464.464 0 0 1 .537-.375.46.46 0 0 1 .38.53l-1.539 8.852a.463.463 0 0 1-.458.382"></path>
    </svg>
</template>

<script>
    export default {
        name: "RateStar",
        props: {
            rating: Number,
            value: Number,
            stars_count: [Number, String],
            clr_prime: String,
            clr_second: String
        },
        computed: {
            starColor() {
                return this.value > this.rating ? this.clr_second : this.clr_prime;
            },
            starWidth() {
                return `${100 / this.stars_count}%`;
            }
        }
    }
</script>

<style lang="scss" scoped>
    .star {
        pointer-events: none;

        path {
            transform-origin: center;
            transform: scale(0.7);
            transition: 0.2s;
        }
    }
</style>
