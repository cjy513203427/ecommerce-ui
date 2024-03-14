<template>
    <div class="container">
        <div class="row">
            <div class="col-12 test-center">
                <h3 class="pt-3">Our Categories</h3>
            </div>
        </div>

        <div class="row">
            <div class="col-3"></div>
            <div class="col-6"></div>
        </div>
    </div>
</template>

<script>

const axios = require("axios");
// import CategoryBox from '@/components/Cateogry/CategoryBox.vue'
export default {
    name: "Category",
    components: {},
    data() {
        return {
            baseURL: "http://localhost:8081",
            categories: []
        };
    },

    methods: {
        async getCategories(){
            await axios.get(`${this.baseURL}/category/list`)
            .then(res => this.categories = res.data)
            .catch(err => console.log(err))
        }
    },

    mounted(){
        this.getCategories()
    }
};
</script>

<style scoped></style>
