<template>
    <div class="container">
        <section class="carousel">
            <h2 class="carousel-title">Previously viewed products 
                <span>
                    <a href="#">View all</a>
                </span>
            </h2>

            <div class="carousel-container">

                <Carousel :items-to-show="2" :breakpoints="breakpoints" class="carousel-01">
                    <Slide
                        v-for="product in products"
                        :key="product.id"
                        
                    >
                        <div class="carousel-item">
                            <div class="carousel-item__img">
                                <img :src=" require('../assets/slide_img/' + product.image)" alt="">
                                <div class="carousel-item__img--sale">
                                    <span>{{ product.sale }}</span>
                                </div>
                                <a class="carousel-item__img--favorite">
                                    <img src="@/assets/icons/like-slider.svg">
                                </a>
                            </div>
                            <div class="carousel-item__descr">
                                <span class="carousel-item__descr--price">{{ product.price }} $ <span>{{ product.oldprice }} $</span></span>
                                <p class="carousel-item__descr--text">{{ product.name }}</p>
                                <a href="#" class="carousel-item__descr--link">{{ product.link }}</a>
                            </div>
                            <div class="carousel-item__raiting">
                                <div class="carousel-item__raiting--items">
                                    <img src="@/assets/icons/star-active-desk.svg">
                                    <img src="@/assets/icons/star-active-desk.svg">
                                    <img src="@/assets/icons/star-active-desk.svg">
                                    <img src="@/assets/icons/star-active-desk.svg">
                                    <img src="@/assets/icons/star-desk.svg">
                                </div>
                                <p class="carousel-item__raiting--reviews">25 reviews</p>
                            </div>
                        </div>
                    </Slide>

                    <template #addons>
                        <Navigation>
                            <button class="carousel__prev">
                                <img class="carousel-icon" src="@/assets/icons/prev-slider.svg">
                            </button>
                            <button class="carousel__next">
                                <img class="carosel-icon" src="@/assets/icons/next.svg">
                            </button>
                        </Navigation>
                    </template>
                </Carousel>
            </div>

            <hr class="carousel-line">
        </section>
    </div>
</template>

<script>
import { Carousel, Navigation, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

export default {
    components: {
        Carousel,
        Slide,
        Navigation
    },
    data() {
        return {
            breakpoints: {
                320: {
                    itemsToShow: 2.1,
                    snapAlign: 'start',
                },
                700: {
                    itemsToShow: 4.5,
                    snapAlign: 'start',
                },
                1024: {
                    itemsToShow: 5,
                    snapAlign: 'start',
                },
                1440: {
                    itemsToShow: 6.5,
                    snapAlign: 'start',
                },
            },
            products: [
                {
                    id: 1,
                    image: "image36.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, Red",
                    link: "Best jeans store",
                    sale: "-12%"
                },
                {
                    id: 2,
                    image: "image33.png",
                    price: 910.15,
                    oldprice: 890.89,
                    name: "Samsung Galaxy S10 8 / 128GB Aquamarine...",
                    link: "Best jeans store",
                    sale: "-15%"
                },
                {
                    id: 3,
                    image: "image31.png",
                    price: 820.15,
                    oldprice: 646.99,
                    name: "Smartphone Apple iPhone 11 64GB, Black",
                    link: "Best jeans store",
                    sale: "-10%"
                },
                {
                    id: 4,
                    image: "image34.png",
                    price: 410.15,
                    oldprice: 546.99,
                    name: "TV box Xiaomi Mi Box S",
                    link: "Best jeans store",
                    sale: "-20%"
                },
                {
                    id: 5,
                    image: "image33.png",
                    price: 910.15,
                    oldprice: 890.89,
                    name: "Samsung Galaxy S10 8 / 128GB Aquamarine...",
                    link: "Best jeans store",
                    sale: "-15%"
                },
                {
                    id: 6,
                    image: "image36.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, red",
                    link: "Best jeans store",
                    sale: "-12%"
                },
                {
                    id: 7,
                    image: "image31.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, red",
                    link: "Best jeans store",
                    sale: "-10%"
                },
                {
                    id: 8,
                    image: "image33.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, red",
                    link: "Best jeans store",
                    sale: "-15%"
                },
                {
                    id: 9,
                    image: "image34.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, red",
                    link: "Best jeans store",
                    sale: "-20%"
                },
                {
                    id: 10,
                    image: "image36.png",
                    price: 810.15,
                    oldprice: 846.99,
                    name: "Smartphone Apple iPhone 11 64GB, red",
                    link: "Best jeans store",
                    sale: "-12%"
                }
            ]
        }
    }
};
</script>

<style lang="scss">
@media (min-width: 320px) {
    .carousel-01 {
        .carousel__prev, .carousel__next {
            display: none;
        }
    }
}

@media (min-width: 1024px) {
    .carousel-01 {
        .carousel__prev {
            position: absolute;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 30px;
            height: 40px;
            left: 5px;
            top: 35%;
            background: #FFFFFF;
            border: 1px solid #CDCDCD;
            border-radius: 3px;
            z-index: 2;
            cursor: pointer;
        }

        .carousel__next {
            position: absolute;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 30px;
            height: 40px;
            right: 0px;
            top: 35%;
            background: #FFFFFF;
            border: 1px solid #CDCDCD;
            border-radius: 3px;
            z-index: 2;
            cursor: pointer;
        }
        .carousel__prev--in-active,
        .carousel__next--in-active {
            display: none;
        }   
    }
}
</style>