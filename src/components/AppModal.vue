<template>
    <div class="modal">
        <div class="modal__body">
            <div @click="close_modal()" class="modal__close-btn">
                <svg viewBox="0 0 174.2 174.2">
                    <path fill="#fff" d="M146.537,1.047c-1.396-1.396-3.681-1.396-5.077,0L89.658,52.849
                        c-1.396,1.396-3.681,1.396-5.077,0L32.78,1.047 c-1.396-1.396-3.681-1.396-5.077,0
                        L1.047,27.702c-1.396,1.396-1.396,3.681,0,5.077l51.802,51.802c1.396,1.396,1.396,3.681,0,5.077
                        L1.047,141.46c-1.396,1.396-1.396,3.681,0,5.077l26.655,26.655c1.396,1.396,3.681,1.396,5.077,0
                        l51.802-51.802 c1.396-1.396,3.681-1.396,5.077,0l51.801,51.801c1.396,1.396,3.681,1.396,5.077,0
                        l26.655-26.655c1.396-1.396,1.396-3.681,0-5.077 l-51.801-51.801c-1.396-1.396-1.396-3.681,0-5.077
                        l51.801-51.801c1.396-1.396,1.396-3.681,0-5.077L146.537,1.047z"></path>
                </svg>
            </div>

            <h2 class="title">How did we do?</h2>
            <p class="paragraph">
                Please let us know how your food delivery was.
                It will really help us to keep improving our service!
            </p>

            <app-rate v-for="question in quiz"
                      :key="question.refer"
                      :refer="question.refer"
                      :label="question.label"
                      @change="setRating">
            </app-rate>

            <div @click="close_modal('submit')" class="btn">Submit feedback</div>
        </div>
    </div>
</template>

<script>
    import AppRate from './AppRate'

    export default {
        name: "AppModal",
        components: {
            AppRate
        },
        data() {
            return {
                ratings: {},
                quiz: {
                    food_rating: {
                        refer: "food",
                        label: "How would you rate your food?"
                    },
                    driver_rating: {
                        refer: "driver",
                        label: "How would you rate your delivery driver?"
                    },
                    experience_rating: {
                        refer: "experience",
                        label: "How would you rate your overall experience?"
                    }
                }
            };
        },
        methods: {
            setRating(rating) {
                this.ratings[`${rating.refer}_rating`] = rating;
            },
            close_modal(submit) {
                this.$emit("close_modal", submit ? this.ratings : {});
            }
        }
    }
</script>

<style scoped lang="scss">
    @import "../scss/variables";

    .modal {
        position: fixed;
        top: 0;
        bottom: 0;
        right: 0;
        left: 0;
        display: flex;
        padding: 16px;
        background-color: rgba(lighten($clr-dark, 45%), .7);
        transition: 0.2s;
        overflow-y: auto;

        &__body {
            position: relative;
            max-width: 645px;
            margin: auto;
            padding: 64px 80px 76px;
            box-sizing: border-box;
            border-radius: 8px;
            background-color: $clr-light;
            box-shadow: 0 10px 10px 0 rgba(0, 0, 0, 0.15),
                0 14px 28px 0 rgba(0, 0, 0, 0.15);

            .btn {
                margin-top: 50px;
            }
        }

        &__close-btn {
            position: absolute;
            top: -13px;
            right: -13px;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 46px;
            height: 46px;
            border-radius: 50%;
            background-color: $clr-dark;
            cursor: pointer;

            svg {
                width: 50%;
                transition: 0.1s;
            }

            &:hover svg {
                transform: scale(1.05);
            }
        }
    }

    @media (max-width: 768px) {
        .modal {
            &__body {
                padding: 50px 40px;

                .btn {
                    margin-top: 40px;
                }
            }
        }
    }

    @media (max-width: 480px) {
        .modal {
            &__body {
                padding: 32px 16px;

                .btn {
                    margin-top: 32px;
                }
            }

            &__close-btn {
                top: -8px;
                right: -8px;
                width: 36px;
                height: 36px;
            }
        }
    }
</style>
