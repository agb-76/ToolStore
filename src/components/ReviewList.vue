<script setup>
import { reactive, ref, computed } from 'vue' 

const props = defineProps({
    reviews: {type: Array, required: true}
})
</script>

<template>

<div class="review-container">
  <h3>Reviews:</h3>
    <ul>
      <li v-for="(review, index) in props.reviews" :key="index">
        {{ review.name }} gave this {{ review.rating }} stars
        <br/>
        "{{ review.review }}"
        <br/>
        <!-- solution -->
        Recommended: {{ review.recommend }}
        <!-- solution -->
      </li>
    </ul>
  </div>

</template>

<style>

</style>