<template>
    <div class="user"
        v-for="user in users" :key="user.id"
    >
        <div class="user-name">
            <div class="user-name__img">
                <img :src="require('../assets/slide_img/' + user.img)" alt="">
            </div>
            <div class="user-name__title">
                <p class="user-name__title--name">{{user.name}}</p>
                <div class="user-name__title--stars">
                    <img src="@/assets/icons/star-active.svg">
                    <img src="@/assets/icons/star-active.svg">
                    <img src="@/assets/icons/star-active.svg">
                    <img src="@/assets/icons/star-active.svg">
                    <img src="@/assets/icons/star.svg">
                </div>
                <p class="user-name__title--date">{{user.date}}</p>
            </div>
        </div>
        <div class="user-name__text">
            <p class="user-name__text--advantages">
                <span>{{user.advantagesName}}</span>
                {{user.advantages}}
            </p>
            <p class="user-name__text--disadvantages">
                <span>{{user.disadvantagesName}}</span>
                {{user.disadvantages}}
            </p>
            <p class="user-name__text--title">
                {{user.text}}
            </p>
        </div>
        <div class="user-name__images">
            <div class="user-name__images--item"
                v-for="items in user.slide" :key="items.id"
            >
                <img :src="items.item" alt="">
            </div>
        </div>

        <div class="user-name__reactions">
            <button v-on:click="like += 1" class="user-name__reactions--like">
                <img src="@/assets/icons/like-btn.svg">
                <span id="count-reaction">{{ like }}</span>
            </button>
            <button class="user-name__reactions--dislike">
                <img src="@/assets/icons/dislike-btn.svg">
                <span id="count-reaction">{{ dislike }}</span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            like: 4,
            dislike: 2,
            users: [
                {
                    id: 1,
                    name: "Jack S.",
                    img: "account1.png",
                    date: "10 July 2020",
                    advantagesName: "Advantages:",
                    advantages: "Excellent product, good quality, nice color, size as indicated, nice price, advise.",
                    disadvantagesName: "Disadvantages:",
                    disadvantages: "Didn't notice",
                    text: "I checked the goods according to the dimensional grid and everything fit, the delivery did not take much time, I am happy with everything, I will order from this seller.",
                    slide: [
                        {
                            id: 1,
                            item: require("../assets/column_img/image44.png")
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
                        },
                        {
                            id: 5,
                            item: require("../assets/column_img/image44.png")
                        },
                        {
                            id: 6,
                            item: require("../assets/column_img/image44.png")
                        }
                    ],
                },
                {
                    id: 2,
                    name: "Marry J.",
                    img: "account2.png",
                    date: "23 Junuary 2021",
                    text: "I checked the goods according to the dimensional grid and everything fit, the delivery did not take much time, I am happy with everything, I will order from this seller.",
                    slide: false
                }
            ]
        }
    }
}
</script>