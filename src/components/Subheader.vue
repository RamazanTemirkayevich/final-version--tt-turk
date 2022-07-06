<template>
    <div class="container">
        <section class="subheader">
            <div class="subheader-nav">
                <a href="#" class="subheader-nav__btn">
                    <img src="@/assets/icons/prev.svg" alt="">
                    Back
                </a>
                <ul class="subheader-nav__list">
                    <li class="subheader-nav__list--link">
                        <img src="@/assets/icons/home-desktop.svg" alt="home">
                    </li>
                    <li class="subheader-nav__list--link">
                        <span>/</span>
                        <a href="#">Categories</a>
                    </li>
                    <li class="subheader-nav__list--link">
                        <span>/</span>
                        <a href="#">Men`s clothing</a>
                    </li>
                    <li class="subheader-nav__list--link">
                        <span>/</span>
                        <a href="#">Jeans</a>
                    </li>
                    <li class="subheader-nav__list--link">
                        <span>/</span>
                        <a href="#">Product #123821</a>
                    </li>
                </ul>
            </div>

            <div class="subheader-name">
                <h2 class="subheader-name__title">Signature gray oversized faux fur shirt</h2>
                <div class="subheader-name__function">
                    <div class="subheader-name__function--stars">
                        <img src="@/assets/icons/star-active-desk.svg">
                        <img src="@/assets/icons/star-active-desk.svg">
                        <img src="@/assets/icons/star-active-desk.svg">
                        <img src="@/assets/icons/star-desk.svg">
                        <img src="@/assets/icons/star-desk.svg">
                    </div>
                    <div class="subheader-name__function--info">
                        <span>3.5</span>
                        <img src="@/assets/icons/circle.svg">
                        <p>25 reviews</p>
                        <img src="@/assets/icons/circle.svg">
                        <p>86 orders</p>
                    </div>
                    <a href="#" class="subheader-name__function--add">
                        <img src="@/assets/icons/add.svg">
                        <a 
                            @click="addTo()"
                            v-bind:class="[Deffered ? 'deffered-btn' : 'deffered-btn__add']"
                        >
                            {{ Deffered ? 'Add to deffered' : 'Item added' }}
                        </a>
                    </a>
                    <p class="subheader-name__function--code">Product code: 123821</p>
                </div>
            </div>

            <hr class="subheader-line">
        </section>
    </div>
</template>

<script>
export default {
    data() {
        return {
            Deffered: true
        }
    },
    methods: {
        addTo() {
            this.Deffered = !this.Deffered
        }
    }
}
</script>