<template>
    <div class="footer">
        <div class="footer-btn">
            <a href="#" class="footer-btn__item"
                v-bind:class="[Active ? 'footer-btn__item' : 'footer-btn__item--add']"
                @click="$refs.alert02
                    .showAlert(
                        'success',
                        'Item added to cart',
                        'Done',
                        'Success 200',
                        'This is the information of something you may know Success.'
                    ),
                    toggleBtn()
                    "
            >
                {{ Active ? 'Add to Shopping Cart' : 'Remove from Cart'}}
            </a>
            <vue-basic-alert 
                :duration="300"
                :closeIn="3500"
                ref="alert02" 
            />
        </div>
        <div class="footer-list">
            <ul class="footer-list__items">
                <li class="footer-list__items--link">
                    <a href="#">
                        <img src="@/assets/icons/home.svg" alt="">
                        <p>Home</p>
                    </a>
                </li>
                <li class="footer-list__items--link">
                    <a href="#">
                        <img src="@/assets/icons/categories.svg" alt="">
                        <p>Categories</p>
                    </a>
                </li>
                <li class="footer-list__items--link">
                    <a href="#">
                        <img src="@/assets/icons/basket.svg" alt="">
                        <p>Shop cart</p>
                    </a>
                </li>
                <li class="footer-list__items--link">
                    <a href="#">
                        <img src="@/assets/icons/favorite.svg" alt="">
                        <p>Favorites</p>
                    </a>
                </li>
                <li class="footer-list__items--link">
                    <a href="#">
                        <img src="@/assets/icons/profile.svg" alt="">
                        <p>Profile</p>
                    </a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import VueBasicAlert from 'vue-basic-alert'

export default {
    components: {
        VueBasicAlert
    },
    data() {
        return {
            Active: true
        }
    },
    methods: {
        toggleBtn: function(){
            this.Active = !this.Active;
            
        }
    }
}
</script>
