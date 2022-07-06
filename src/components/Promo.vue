<template>
    <section class="promo">
        <div class="promo-img">
            <swiper
                :pagination="{
                    type: 'fraction'
                }"          
                :modules="modules"                
                class="swipe"
            >
                <swiper-slide class="swiper-slide" v-for="items in images" :key="items.id">
                    <img :src="items.item">
                </swiper-slide>
            </swiper>
        </div>
        <div class="promo-back">
            <a href="#">
                <img src="@/assets/icons/back.svg" alt="">
            </a>
        </div>
        <div class="promo-like">
            <a href="#">
                <img src="@/assets/icons/like.svg" alt="">
            </a>
        </div>

        <div class="container">
            <div class="promo-container">
                <div class="promo-img__desktop">
                    <div class="promo-img__desktop--column">
                        <a class="column-img" v-on:click="activetab=1" v-bind:class="[ activetab === 1 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image44.png" alt="column img">
                        </a>
                        <a class="column-img" v-on:click="activetab=2" v-bind:class="[ activetab === 2 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image48.png" alt="column img">
                        </a>
                        <a class="column-img" v-on:click="activetab=3" v-bind:class="[ activetab === 3 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image49.png" alt="column img">
                        </a>
                        <a class="column-img" v-on:click="activetab=4" v-bind:class="[ activetab === 4 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image50.png" alt="column img">
                        </a>
                        <a class="column-img" v-on:click="activetab=5" v-bind:class="[ activetab === 5 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image44.png" alt="column img">
                        </a>
                        <a class="column-img" v-on:click="activetab=6" v-bind:class="[ activetab === 6 ? 'active' : '' ]">
                            <img src="@/assets/column_img/image48.png" alt="column img">
                        </a>
                    </div>

                    <div class="promo-img__desktop--main">    
                        <img v-if="activetab === 1" class="tabcontent" src="@/assets/image44.png" alt="promo image">
                        <img v-if="activetab === 2" class="tabcontent" src="@/assets/column_img/image48.png" alt="promo image">
                        <img v-if="activetab === 3" class="tabcontent" src="@/assets/column_img/image49.png" alt="promo image">
                        <img v-if="activetab === 4" class="tabcontent" src="@/assets/column_img/image50.png" alt="promo image">
                        <img v-if="activetab === 5" class="tabcontent" src="@/assets/column_img/image44.png" alt="promo image">
                        <img v-if="activetab === 6" class="tabcontent" src="@/assets/column_img/image48.png" alt="promo image">
                    </div>

                </div>

                <div class="promo-descr">
                    <div class="promo-descr__retail">
                        <p class="promo-descr__retail--text">Retail price</p>
                        <span class="price">14,25 $</span> <span class="old-price">15,35 $</span>
                    </div>
                    <div class="promo-descr__wholesale">
                        <p class="promo-descr__wholesale--text">Wholesale price</p>
                        <span class="price">12,50 $</span>
                    </div>
                    <a class="promo-descr__btn">
                        Buy now
                    </a>
                </div>

                <div class="promo-descr-desktop">
                    <div class="promo-color"
                        v-for="color in colors" :key="color.id"
                    >
                        <p class="promo-color__name">Color: <span>{{ color.item }}</span></p>
                        <div class="promo-color__images">
                            <div class="promo-color__images--item">
                                <img src="@/assets/color-img.png" alt="color">
                            </div>
                            <div class="promo-color__images--item">
                                <img src="@/assets/color-img2.png" alt="color">
                            </div>
                        </div>
                    </div>
                    <div class="promo-size">
                            <Tab :isSelected="selected === 'xs'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">XS</span>
                            </Tab>
                            <Tab :isSelected="selected === 's'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">S</span>
                            </Tab>
                            <Tab :isSelected="selected === 'm'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">M</span>
                            </Tab>
                             <Tab :isSelected="selected === 'l'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">L</span>
                            </Tab>
                             <Tab :isSelected="selected === 'xl'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">XL</span>
                            </Tab>
                             <Tab :isSelected="selected === 'xxl'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">XXL</span>
                            </Tab>
                             <Tab :isSelected="selected === 'xxxl'" >
                                Size:
                                <span style="color: black; margin-left: 5px;">XXXL</span>
                            </Tab>
                        <TabNav :tabs="['xs', 's', 'm', 'l', 'xs', 'xxl', 'xxxl']" :selected="selected" @selected="setSelected" />
                        <!-- <p class="promo-size__name">
                            Size: <span>{{}}</span>
                        </p>

                        <div class="promo-size__items">
                            <div class="promo-size__items--index"
                                v-for="size of sizes" 
                                :key="size.id">{{ size.value }}
                            </div>
                        </div> -->
                    </div>
                    <div class="promo-counter">
                        <p class="promo-counter__title">Amount: <span>{{ count }}</span></p>
                        <div class="promo-counter__elements">
                            <div class="counter">
                                <button @click="if (count > 0) count--;" class="minus">-</button>
                                <span>{{ count }}</span>
                                <button @click="count++" class="plus">+</button>
                            </div>
                            <p class="amount">12451 pcs. in stock</p>
                        </div>
                    </div>
                    <div class="promo-delivery">
                        <div class="promo-delivery-container">
                            <p class="promo-delivery-container__price">Delivery: 5,25 $</p>
                            <div class="promo-delivery-container__dropdown">
                                <select name="delivery" id="">
                                    <option value="1">To Isnabbul via PONNY EXPRESS</option>
                                </select>
                                <img src="@/assets/icons/dropdown.svg">
                            </div>
                            <p class="promo-delivery-container__time">Estimated delivery time: 
                                <span>25/08</span>
                                <img src="@/assets/icons/question.svg" alt="">
                            </p>
                        </div>
                    </div>
                    <a href="#characteristics" class="promo-detail">View detailed characteristics</a>
                </div>

                <div class="promo-blocks">
                    <div class="promo-price-desktop">
                        <div class="promo-price-desktop__container">
                            <div class="promo-price-desktop__retail">
                                <p class="promo-price-desktop__retail--text">Retail price</p>
                                <span class="price">14,25 $</span> <span class="old-price">15,35 $</span>
                            </div>
                            <div class="promo-price-desktop__wholesale">
                                <p class="promo-price-desktop__wholesale--text">Wholesale price</p>
                                <span class="price">12,50 $</span>
                            </div>
                            <a href="#" class="promo-price-desktop__buy"
                                v-bind:class="[isActive ? 'promo-price-desktop__buy' : 'promo-price-desktop__buy--add']"
                                @click="$refs.alert
                                    .showAlert(
                                        'success',
                                        'Item added to cart',
                                        'Done',
                                        'Success 200',
                                        'This is the information of something you may know Success.'
                                    ), 
                                    toggleClass()
                                    "
                            >
                                {{ isActive ? 'Add to Shopping Cart' : 'Remove from Cart'}}
                            </a>
                            <a class="promo-price-desktop__btn">
                                Buy now
                            </a>

                            <vue-basic-alert 
                                :duration="300"
                                :closeIn="3500"
                                ref="alert" 
                            />

                            <vue-basic-alert 
                                :duration="300"
                                :closeIn="3500"
                                ref="alert02" 
                            />
                        </div>
                    </div>

                    <div class="promo-brand-desktop">
                        <div class="promo-brand-desktop__container">
                            <div class="brand-img">
                                <img src="@/assets/look.png" alt="">
                            </div>
                            <div class="brand-title">
                                <p class="brand-title__name">New Look</p>
                                <div class="brand-title__items">
                                    <div class="brand-title__items--raiting">
                                        <img src="@/assets/icons/star-active-desk.svg">
                                        <img src="@/assets/icons/star-active-desk.svg">
                                        <img src="@/assets/icons/star-active-desk.svg">
                                        <img src="@/assets/icons/star-desk.svg">
                                        <img src="@/assets/icons/star-desk.svg">
                                    </div>
                                    <span>3.5</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <hr class="promo-line">

                <div class="promo-name">
                    <div class="promo-name__items">
                        <h2 class="promo-name__items--title">Signature gray oversized faux fur shirt</h2>
                        <div class="promo-name__items--img">
                            <img src="@/assets/brand.png" alt="">
                        </div>
                    </div>

                    <div class="promo-name__descr">
                        <div class="promo-name__descr--raiting">
                            <div class="raiting-stars">
                                <img src="@/assets/icons/star-active.svg" alt="">
                                <img src="@/assets/icons/star-active.svg" alt="">
                                <img src="@/assets/icons/star-active.svg" alt="">
                                <img src="@/assets/icons/star-active.svg" alt="">
                                <img src="@/assets/icons/star.svg" alt="">
                            </div>
                            <span class="raiting-text">485 reviews</span>
                        </div>
                        <p class="promo-name__descr--code">Product code: <span>2138815</span></p>
                        <p class="promo-name__descr--text">Bought more than 512882 times</p>
                    </div>
                </div>

                <hr class="promo-line">

                <div class="promo-information">
                    <p class="promo-infromation__price">Delivery: <span>5,25 $</span></p>
                    <p class="promo-infromation__time">Estimated delivery time: <span>25/08</span></p>
                    <p class="promo-infromation__brand">
                        Seller: 
                        <span>New Look</span>
                        <img src="@/assets/icons/info.svg" alt="">
                    </p>
                </div>

                <hr class="promo-line">
            </div>
        </div>
    </section>
</template>

<script>
import SwiperCore, { Pagination, Navigation } from 'swiper'
import { Swiper, SwiperSlide } from 'swiper/vue'
import VueBasicAlert from 'vue-basic-alert'
import TabNav from './TabNav.vue'
import Tab from './Tab.vue'

import "swiper/swiper.scss";
import "swiper/components/pagination/pagination.scss";
import "swiper/components/navigation/navigation.scss";

SwiperCore.use([Navigation, Pagination])

export default {
    components: {
        Swiper,
        SwiperSlide,
        VueBasicAlert,
        TabNav,
        Tab
    },
    data() {
        return {
            currentSize: 'x',
            count: 0,
            activetab: 1,
            selected: 'Home',
            images: [
                {   
                    id: 1,
                    item: require("../assets/image44.png")
                },
                {
                    id: 2,
                    item: require("../assets/column_img/image48.png")
                },
                {
                    id: 3,
                    item: require("../assets/column_img/image49.png")
                },
                {
                    id: 4,
                    item: require("../assets/column_img/image50.png")
                }
            ],
            colors: [
                {
                    id: 1,
                    item: "Blue"
                }
            ],
            sizes: [
                {
                    id: 1,
                    value: 'xs'
                },
                {
                    id: 2,
                    value: 's'
                },
                {
                    id: 3,
                    value: 'm'
                },
                {
                    id: 4,
                    value: 'l'
                },
                {
                    id: 5,
                    value: 'xl'
                },
                {
                    id: 6,
                    value: 'xxl'
                },
                {
                    id: 7,
                    value: 'xxxl'
                }
            ],
            isActive: true,
            cur: 7
        }
    },
    methods: {
        toggleClass: function(){
            this.isActive = !this.isActive;
            
        },
        setSelected(tab) {
            this.selected = tab;
        }
    }
}
</script>