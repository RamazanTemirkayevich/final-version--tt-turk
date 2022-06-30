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
            <button @click="likeReaction" class="user-name__reactions--like">
                <img src="@/assets/icons/like-btn.svg">
                <span id="count-reaction">{{ user.like }}</span>
            </button>
            <button @click="dislikeReaction" class="user-name__reactions--dislike">
                <img src="@/assets/icons/dislike-btn.svg">
                <span id="count-reaction">{{ user.dislike }}</span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            clicked: false,
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
                    like: 2,
                    dislike: 0
                },
                {
                    id: 2,
                    name: "Marry J.",
                    img: "account2.png",
                    date: "23 Junuary 2021",
                    text: "I checked the goods according to the dimensional grid and everything fit, the delivery did not take much time, I am happy with everything, I will order from this seller.",
                    advantagesName: "Advantages:",
                    advantages: "",
                    disadvantagesName: "",
                    disadvantages: " ",
                    slide: false,
                    like: 0,
                    dislike: 0
                }
            ]
        }
    },
    methods: {
        likeReaction () {
            if (!this.clicked) {
                this.clicked = true
                this.users[0].like++
            } else {
                this.clicked = false
                this.users[0].like--
            }
        },
        dislikeReaction () {
            if (!this.clicked) {
                this.clicked = true
                this.users[0].dislike++
            } else {
                this.clicked = false
                this.users[0].dislike--
            }
        }
    }
}
</script>