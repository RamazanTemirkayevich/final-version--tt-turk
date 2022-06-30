<template>
    <div class="container">
        <section class="description">
            <h2 class="description-title">Description</h2>
            <!-- <div class="description-text">
                <p class="description-text__title">
                    <span class="description-text__title--mobile">
                        Basic slim jeans with a regular fit. Closure and belt loops with contrast stitching. The <span v-show="descriptionOpen" class="hide-text">yoke at the back provides a perfect fit on the hips. Aged denim, with bleached spots and moderate fading, immediately grabs attention. Slightly narrowed at the bottom, the model tightly fits the figure, visually stretches the silhouette and slims. Durable denim is breathable, non-irritating, hygroscopic, easy to clean and practical. These jeans are comfortable all day long. A versatile casual piece, perfect for city life. Skinny basic jeans look great with fitted shirts and oversized shirts, jumpers and T-shirts. Shoes will suit them very different - from sports sneakers and sneakers to lace-up boots or brogues. Slim jeans are a practical and comfortable option that should definitely be in your wardrobe.
                        </span> 
                    </span>
                    <span class="description-text__title--desktop">
                        Basic slim jeans with a regular fit. Closure and belt loops with contrast stitching. The yoke at the back provides a perfect fit on the hips. Aged denim, with bleached spots and moderate fading, immediately grabs attention. Slightly narrowed at the bottom, the model tightly fits the figure, visually stretches the silhouette and slims. Durable denim is breathable, non-irritating, hygroscopic, easy to clean and practical. These jeans are comfortable all day long. A versatile casual piece, perfect for city life. Skinny basic jeans look great with fitted shirts and oversized shirts, jumpers and T-shirts. Shoes will suit them very different - from sports sneakers and sneakers to lace-up boots or brogues. Slim jeans are a practical and comfortable option that should definitely be in your wardrobe.
                    </span>
                </p>
            </div> -->

            <VueSlickCarousel 
                ref="c1"
                :asNavFor="$refs.c2"
                :focusOnSelect="true"
            >
                <div><h3>1</h3></div>
                <div><h3>2</h3></div>
                <div><h3>3</h3></div>
                <div><h3>4</h3></div>
            </VueSlickCarousel>

            <!-- <VueSlickCarousel
                ref="c2"
                :asNavFor="$refs.c1"
                :slidesToShow="4"
                :focusOnSelect="true"
            >
                <div><h3>1</h3></div>
                <div><h3>2</h3></div>
                <div><h3>3</h3></div>
                <div><h3>4</h3></div>
            </VueSlickCarousel> -->

            <p @click="toggleDescription" class="description-show">{{ descriptionOpen ? 'Hide Description' : 'Expand Description' }}</p>

            <hr class="description-line">

            <div class="description-characteristics">
                <h2 class="description-characteristics__title">Characteristics</h2>
                <div class="description-characteristics__items">
                    <p>Season</p>
                    <span>Demi-season</span>

                    <hr>

                    <p>Material</p>
                    <span>Cotton</span>

                    <hr>

                    <p>Material composition</p>
                    <span>100% cotton</span>

                    <div v-show="featuresOpen" class="hide-characteristics">
                        <hr>


                        <p>Collection</p>
                        <span>Spring-summer 2020</span>

                        <hr>

                        <p>Model size in photo</p>
                        <span>50</span>

                        <hr>

                        <p>The growth of the model in the photo</p>
                        <span>181 cm</span>

                        <hr>

                        <p>A type</p>
                        <span>Jeans</span>

                        <hr>

                        <p>Brand in clothing and footwear</p>
                        <span>JeansShop</span>

                        <hr>
                    </div>

                    <p @click="toggleFeatures" class="characteristics-show">{{ featuresOpen ? 'Hide Characteristics' : 'Expand Characteristics' }}</p>

                    <hr>
                </div>
                <div class="description-characteristics__box">
                    <div class="box-items">
                        <Characteristics/>
                    </div>
                    <div class="box-items">
                        <Characteristics/>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import Characteristics from './Characterisctics.vue'

import VueSlickCarousel from 'vue-slick-carousel'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name: 'Description',
    components: {
        Characteristics,
        VueSlickCarousel
    },
    data() {
        return {
            featuresOpen: false,
            descriptionOpen: false
        }
    },
    methods: {
        toggleFeatures () {
            this.featuresOpen = !this.featuresOpen
        },
        toggleDescription () {
            this.descriptionOpen = !this.descriptionOpen
        }
    }
}
</script>

<style lang="scss">
.carousel {
    .carousel__item {
    min-height: 200px;
    width: 100%;
    background-color: var(--vc-clr-primary);
    color:  var(--vc-clr-white);
    font-size: 20px;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
    }

    .carousel__slide {
    padding: 10px;
    }

    .carousel__prev,
    .carousel__next {
    box-sizing: content-box;
    border: 5px solid white;
    }

    .pagination {
        .carousel__pagination {
            &-button {
                display: flex;
                flex-direction: row;
                justify-content: center;
                align-items: center;
                padding: 0px;
                gap: 10px;

                width: 148px;
                height: 187px;

                /* --gray-light */

                background: url("/assets/column_img/image44.png");
                border-radius: 5px;
            }
        }
    }
}
</style>
