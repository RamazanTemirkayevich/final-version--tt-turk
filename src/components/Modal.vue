<template>
    <div class="modal">
        <div class="modal-box">
            <slot />
        </div>
    </div>
</template>

<style lang="scss">
    @media (min-width: 320px) {
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 99;
            background-color: rgba(0, 0, 0, 0.2);
            
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 35px 10px;

            &-box {
                width: 100%;
                height: 100%;
                padding: 15px;
                display: flex;
                align-items: center;
                justify-content: center;
                background: #FFFFFF;
                border-radius: 10px;

                &__container {
                    width: 100%;
                    height: 100%;

                    &>form {
                        display: flex;
                        flex-direction: column;
                        justify-content: space-between;
                        width: 100%;
                        height: 100%;

                        .modal-box__container--title {
                            display: flex;
                            width: 100%;
                            justify-content: space-between;

                            .modal-name {
                                font-weight: 500;
                                font-size: 20px;
                                line-height: 23px;
                                color: #0A0A0A;
                            }

                            @media (min-width: 1440px) {
                                .modal-name {
                                    font-size: 28px;
                                }
                            }

                            .modal-close {
                                border: none;
                                background: none;
                                cursor: pointer;
                                outline: none;
                            }
                        }

                        .modal-box__container--raiting {
                            display: flex;
                            flex-direction: column;

                            .raiting-title {
                                font-weight: 500;
                                font-size: 14px;
                                line-height: 19px;
                                color: #404040;                           
                            }

                            @media (min-width: 1440px) {
                                .raiting-title {
                                    font-size: 18px;
                                }
                            }

                            .raiting-stars {
                                margin-top: 7px;
                                width: 135px;
                                display: flex;
                                justify-content: space-between;

                                &>img {
                                    width: 22.22px;
                                }
                            }

                            @media (min-width: 1024px) {
                                .raiting-stars {
                                    width: 212px;

                                    &>img {
                                        width: 39.44px;
                                        // height: 44.45px;
                                    }
                                }
                            }

                            // @media (min-width: 1440px) {
                            //     .raiting-stars {
                            //         width: 270px;

                            //         &>img {
                            //             width: 46.44px;
                            //         }
                            //     }
                            // }
                        }

                        .advantages-form, .disadvantages-form, .comment-form, .upload-images {
                            display: flex;
                            flex-direction: column;

                            &__title {
                                font-weight: 500;
                                font-size: 14px;
                                line-height: 19px;
                                color: #404040;
                            }

                            // @media (min-width: 1440px) {
                            //     &__title {
                            //         font-size: 18px;
                            //     }
                            // }

                            &>input {
                                margin-top: 7px;
                                width: 100%;
                                height: 38px;
                                text-indent: 15px;
                                background: #FFFFFF;
                                border: 2px solid #EEEEEE;
                                border-radius: 7px;
                                outline: none;
                                gap: 10;
                                -webkit-appearance: none; 
                            }

                            // @media (min-width: 1440px) {
                            //     &>input {
                            //         height: 45px;
                            //     }
                            // }

                            &>input:hover {
                                border: 2px solid $main-color;
                            }

                            .comment-form__input {
                                margin-top: 7px;
                                width: 100%;
                                height: 110px;
                                text-indent: 15px;
                                padding-top: 15px;
                                background: #FFFFFF;
                                border: 2px solid #EEEEEE;
                                border-radius: 7px;
                                outline: none;
                                -webkit-appearance: none;
                                resize: none;
                            }

                            // @media (min-width: 1440px) {
                            //     .comment-form__input {
                            //         height: 135px;
                            //     }
                            // }

                            .comment-form__input:hover {
                                border: 2px solid $main-color;
                            }

                            &__btn {
                                margin-top: 7px;
                                display: flex;
                                align-items: center;
                                justify-content: center;
                                width: 100%;
                                height: 50px;
                                background: #FAFAFA;
                                border-radius: 6.25px;
                                border: none;
                            }

                            @media (min-width: 1024px) {
                                &__btn {
                                    width: 108.74px;
                                    height: 108.74px;
                                }
                            }

                            // @media (min-width: 1440px) {
                            //     &__btn {
                            //         width: 138.74px;
                            //         height: 138.74px;
                            //     }
                            // }
                        }

                        .modal-btn {
                            display: flex;
                            flex-direction: row;
                            justify-content: center;
                            align-items: center;
                            width: 100%;
                            height: 40px;
                            background: $main-color;
                            border-radius: 5px;

                            font-weight: 500;
                            font-size: 18px;
                            line-height: 21px;
                            color: #FFFFFF;
                        }

                        @media (min-width: 1024px) {
                            .modal-btn {
                                width: 230px;
                                font-size: 14px;
                                height: 50px;
                            }
                        }

                        // @media (min-width: 1440px) {
                        //     .modal-btn {
                        //         width: 250px;
                        //         font-size: 18px;
                        //     }
                        // }
                    }
                }
            }

            @media (min-width: 1024px) {
                &-box {
                    width: 561px;
                    height: 696px;
                    padding: 30px;
                }
            }

            // @media (min-width: 1440px) {
            //     &-box {
            //         width: 670px;
            //         height: 866px;
            //     }
            // }

            // @media (min-width: 1440px) {
            //     &-box {
            //         width: 670px;
            //         height: 770px;
            //         padding: unset;

            //         &__container {
            //             width: 600px;
            //             height: 700px;

            //             &--raiting {
            //                 margin-top: 25px;
            //             }

            //             &>form {
            //                 .modal-btn {
            //                     margin-top: 25px;
            //                 }
            //             }
            //         }
            //     }
            // }
        }
    }
</style>