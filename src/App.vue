<template>
    <div id="app">
        <div @click="openModal" class="btn btn--flat">Open popup</div>

        <transition name="modal">
            <app-modal v-if="modalIsOpen" @close_modal="close_modal"></app-modal>
        </transition>

        <div class="json">{{ json }}</div>
    </div>
</template>

<script>
    import AppModal from './components/AppModal'

    export default {
        name: 'app',
        components: {
            AppModal
        },
        data() {
            return {
                modalIsOpen: true,
                ratings: {},
            };
        },
        computed: {
            json() {
                if (!this.ratings || !Object.keys(this.ratings).length) return "";

                return JSON.stringify(this.ratings, undefined, 4);
            }
        },
        methods: {
            openModal() {
                this.modalIsOpen = true;
            },
            close_modal(ratings) {
                this.modalIsOpen = false;
                this.ratings = ratings;
            }
        }
    }
</script>

<style lang="scss">
    @import "scss/style.scss";

    #app {
        padding: 16px;
        font-family: $font-sans;
        color: $clr-dark;
        *::selection {
            background-color: rgba(scale_color($clr-prime, hue, 100%), .25);
        }
    }
</style>
