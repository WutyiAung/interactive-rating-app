<template>
    <div class="card-wrapper">
        <div class="card-content" v-if="!isSubmitted">
            <div class="star">
                <i class="fas fa-star" style="color: gold"></i>
            </div>
            <h1>How did we do</h1>
            <p>please let us know how we did with your support appreciated to help us improve our offering</p>
            <div class="rating-wrap">
            <div v-for="(rating, index) in ratingNumbers" :key="rating"
             class="rating" @click="selectRating(index)"
             :class="{ 'selected-rating' : rating.selected }"
             >
                {{ rating.rating }}
            </div>
            </div>
            <button @click="submitForm">Submit</button>
        </div>
        <div class="card-content thank-you" v-else>
            <img src="../assets/thank.png" alt="">
            <div class="selection">
                <span>You selected {{ selectedValue }} out of 5</span>
            </div>
            <h1>Thank you</h1>
            <p>please let us know how we did with your support appreciated to help us improve our offering</p>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
let selectedValue = ref(null);
let isSubmitted = ref(false);

let ratingNumbers = ref([
    {
        rating: 1,
        selected: false,
    },
    {
        rating: 2,
        selected: false,
    },
    {
        rating: 3,
        selected: false,
    },
    {
        rating: 4,
        selected: false,
    },
    {
        rating: 5,
        selected: false,
    }
])
let selectRating = (index) => {
    ratingNumbers.value.forEach( item => item.selected = false);
    ratingNumbers.value[index].selected = true;
    selectedValue.value = ratingNumbers.value[index].rating;
}
let submitForm = () => {
    isSubmitted.value = true;
}
</script>

<style>
.card-wrapper {
    height: 100vh;
    display: grid;
    place-items: center;
    background-color: var(--very-dark-blue);
}

.card-content {
    background-color: var(--dark-blue);
    color: #fff;
    max-width: 450px;
    width: 100%;
    padding: 40px;
    border-radius: 20px;
}

p {
    color: var(--light-grey);
    line-height: 1.6;
    margin-bottom: 30px;
}

.star {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: grid;
    place-items: center;
    background-color: var(--medium-grey-2);
    margin-bottom: 25px;
}

h1 {
    font-size: 28px;
    margin-bottom: 16px;
}

.rating-wrap {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    margin-bottom: 20px;
}

.rating {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: grid;
    place-items: center;
    background-color: var(--medium-grey-2);
    margin-bottom: 25px;
    color: var(--light-grey);
    transition: 200ms ease all;
}

.selected-rating {
    background-color: var(--medium-grey);
    color: white;
}

.rating:hover {
    background-color: var(--orange);
    color: var(--white);
    cursor: pointer;
}

button {
    padding: 12px;
    border-radius: 20px;
    border: none;
    background-color: var(--orange);
    color: white;
    width: 100%;
    text-transform: uppercase;
    font-size: 16px;
    transition: 200ms ease all;
}

button:hover {
    background: var(--white);
    color: var(--orange);
    cursor: pointer;
}
.thank-you{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}
.thank-you img{
    margin-bottom: 30px;
    width: 30%;
    height: 30%;
}
.selection{
    background-color: var(--medium-grey-2);
    color: var(--orange);
    padding: 8px 16px;
    font-size: 14px;
    border-radius: 20px;
    margin-bottom: 40px;
}
.thank-you p{
    margin-bottom: 0;
}
</style>