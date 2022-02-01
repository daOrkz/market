<template>
<div class="flex">
  <div class="left">
    <app-btn
      v-for="(category, ind) in allCategories"
      :key="category"
      :category="category"
      @click="activCategory(ind)"
    > {{category}} </app-btn>
    <button @click="requestCategory">Test</button>
  </div>
  <div class="right">
    <app-goods
      v-for="good in goodsInCategory"
      :key="good.id"
      :good-obj="good"
    ></app-goods>
  </div>
</div>
</template>

<script>
import AppBtn from "./components/AppBtn.vue"
import AppGoods from './components/AppGoods.vue'; 

export default {
  name: 'App',
  data() {
    return {
      allCategories: null,
      currentCategory: '',
      goodsInCategory: ''
    }
  },
  methods: {
    log() {
      console.log("123");
    },
    activCategory(arg1) {
      this.active(arg1)
      this.requestCategory()
    },
    async requestCategories() {
      const request = await fetch('https://fakestoreapi.com/products/categories')
      this.allCategories = await request.json()
    },
    async requestCategory() {
      const request = await fetch(`https://fakestoreapi.com/products/category/${this.currentCategory}`)
      this.goodsInCategory = await  request.json()
      console.log(this.goodsInCategory);
    },
    active(ind) {
      this.currentCategory = this.allCategories[ind]
    }
  },
   beforeMount() {
    this.requestCategories() 
  },
  components: {AppBtn, AppGoods,}
}
</script>

<style>

</style>
