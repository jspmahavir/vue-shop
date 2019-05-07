<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-title">{{ product.title }}</h5>
            <!-- <img :src=product.thumbImg> -->
            <p class="text-center text-muted card-text display-4">$ {{ Number(product.price).toFixed() }}</p>
            <button :disabled="isInCart" @click="addtocart" class="btn btn-primary form-control">
                {{ isInCart ? 'Added to cart..' :  'Add to cart' }}
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['product', 'isInCart'],
        methods: {
        addtocart() {
            this.$emit('add-to-cart',this.title)
        }
       }
    }
</script>