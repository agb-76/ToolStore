<script setup>
import { reactive, ref, computed } from 'vue' 

const emit = defineEmits(['updateCart'])

const props = defineProps({
    premiun: {type: Boolean, required: true}
})

const product = ref({
    name: "Socks",
    description: "xxx",
    stock: 11,
    onSale: true,
    details: ['x','y','z'],
    variants: [
        {id:1, color:'green', quantity: 11, image:"https://raw.githubusercontent.com/Code-Pop/Intro-to-Vue-3/L6-start/assets/images/socks_green.jpg"},
        {id:2, color:'blue',quantity:0, image:"https://raw.githubusercontent.com/Code-Pop/Intro-to-Vue-3/L6-start/assets/images/socks_blue.jpg"}
    ],
    sizes: [1,2,3,4,5],
    brand: "vue",
    selectedVariant: 0
})

function add(){
    emit('updateCart', product.value.variants[product.value.selectedVariant].id)
    product.value.variants[product.value.selectedVariant].quantity--
}

function updateVariant(index){
    product.value.selectedVariant = index
    product.value.image = variantImage
}


const title = computed(
    () => {
        return product.value.brand + ' ' + product.value.name
    }
)

const imageC = computed(() =>{
    return product.value.variants[product.value.selectedVariant].image
})

const inStockC = computed(() =>{
    return product.value.variants[product.value.selectedVariant].quantity
})

const shipping = computed(() =>{
    if(props.premiun)
        return "Free"
    else
        return "2.99"
})
</script>

<template>
<div class="product-display">
    <div class="product-container">
        <div class="product-image">
            <img :src="imageC" alt="Imagen">
        </div>
        <div class="product-info">
            <h1>{{title}}</h1>
            <p>{{product.description}}</p>
            <p v-if="inStockC > 10">In Stock</p>
            <p v-else-if="inStockC <= 10 && inStockC > 0">Almost sold out!</p>
            <p v-else>Out of Stock</p>
            <p v-show="product.onSale">On Sale!</p>

            <p>{{shipping}}</p>

            <ul>
                <li v-for="item in product.details">
                    {{item}}
                </li>
            </ul>
            <div class="color-circle"  
                v-for="(variant, index) in product.variants" 
                :key="variant.id" 
                @mouseover="updateVariant(index)" 
                :style="{backgroundColor: variant.color}"></div>
            <ul>
                <li v-for="size in product.sizes">{{size}}</li>
            </ul>

            <button class="button" :disabled="!inStockC" :class="{disabledButton: !inStockC}" @click="add">Add to Cart</button>
        </div>
    </div>
</div>
</template>

<style>

</style>