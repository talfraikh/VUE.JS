<template>
    <b-col md="7" class="m-3">
        <div>
            <b-card header="List Product">
                <b-card-group deck>
                    <b-card
                        style="min: width: 50%; flex: none !important; width: 45%;"
                        :border-variant="product.inventoryStatus? 'success': 'danger'"
                        align="center"
                        v-for="product in products" :key="product.id"
                        class="mb-3"
                    >
                        <b-badge :variant="product.inventoryStatus? 'success': 'danger'" class="mb-3">{{product.inventoryStatus ? 'In Stock': 'Out Of Stock'}}</b-badge>
                        <b-card-text><b>Name: </b>{{product.name}}</b-card-text>
                        <b-card-text><b>Price: </b>{{product.price}}</b-card-text>
                        <b-card-text><b>Brand: </b>{{product.brand}}</b-card-text>
                        <hr/>
                        <b-row>
                            <b-col>
                                <b-button variant="danger" @click="deleteProduct(product.id)"><i class="fa fa-trash"></i></b-button>
                            </b-col>
                            <b-col>
                                <UpdateProduct :product="product" @updateProduct="updateProduct"/>
                            </b-col>
                        </b-row>
                    </b-card>
                    
                </b-card-group>
            </b-card>
        </div>
    </b-col>
</template>

<script>
import UpdateProduct from './UpdateProduct.vue'
export default {
  props: ['products'],
  components: {
    UpdateProduct
  },
  methods: {
    deleteProduct(productId) {
      this.$emit('deleteProduct', productId);
    },
    updateProduct(updatedProduct) {
      this.$emit('updateProduct', updatedProduct);
    }
  }
}
</script>

<style>

</style>