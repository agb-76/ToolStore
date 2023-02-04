<script setup>
import { reactive, ref, computed } from 'vue' 

const emit = defineEmits(['review-submitted'])
const productReview = ref({
    name :"",
    review : "",
    rating : null,
    recomended : null,
})

function onSubmit(){
    if(productReview.value.name === '' || productReview.value.review === '' || productReview.value.rating === null || productReview.value.recomended === null){
        alert('Review is incomplete. Please fill out every field.')
        return
    }

    emit('review-submitted',productReview)

    productReview.value.name = ''
    productReview.value.review = ''
    productReview.value.rating = null
    productReview.value.recomended = null
}
</script>

<template>
<form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="productReview.name">
    <label for="review">Review:</label>      
    <textarea id="review" v-model="productReview.review"></textarea>
    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="productReview.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>
    <!-- solution -->
    <label for="recommend">Would you recommend this product?</label>
    <select id="recommend" v-model="productReview.recomended">
      <option>Yes</option>
      <option>No</option>
    </select>
    <!-- solution -->   
    <input class="button" type="submit" value="Submit">  
  </form>

</template>

<style>

</style>