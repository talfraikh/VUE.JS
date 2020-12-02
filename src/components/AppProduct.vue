<template>
    <b-col md="4" class="m-3">
        <div>
            <b-card header="Add Product">
                <b-card-body>
                    <b-form autocomplete="off">
                        <b-form-group
                            label="Name"
                        >
                            <b-form-input v-model="form.name" id="name" name="name" trim></b-form-input>
                        </b-form-group>
                        <b-form-group
                            label="Price ($)"
                        >
                            <b-form-input v-model="form.price" id="price" name="price" trim></b-form-input>
                        </b-form-group>
                        <b-form-group
                            label="Brand"
                        >
                            <b-form-input v-model="form.brand" id="brand" name="brand" trim></b-form-input>
                        </b-form-group>
                        <b-form-group label="Ineventry ?">
                            <b-form-radio v-model="form.inventryStatus" name="inventryStatus" value="true">In Stock</b-form-radio>
                            <b-form-radio v-model="form.inventryStatus" name="inventryStatus" value="false">Out Of Stock</b-form-radio>
                        </b-form-group>
                    </b-form>
                </b-card-body>
                <b-button block variant="primary" @click="addProduct">Add Product</b-button>
            </b-card>
        </div>
    </b-col>
</template>

<script>
export default {
    data() {
        return {
            form: {
                name: '',
                price: '',
                brand: '',
                inventryStatus: ''
            },
            submitted: false
        }
    },
    methods: {
        addProduct() {
            this.submitted = true;
            this.$emit('addProduct', {
                name: this.form.name,
                price: '$' + this.form.price,
                brand: this.form.brand,
                inventryStatus: this.form.inventryStatus == 'true'
            });
            this.form = {
                name: '',
                price: '',
                brand: '',
                inventryStatus: ''
            };
            this.submitted = false;
        }
    }
    
}
</script>

<style>

</style>