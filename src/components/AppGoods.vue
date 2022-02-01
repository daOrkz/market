<template>
  <div class="card">
    <h4> {{goodObj.title}} </h4>
    <img :src="goodObj.image" alt="" class="img-good">
    <h3> {{goodObj.price}} $ </h3>
  </div>
</template>

<script>
export default {
  props: {
    goodObj: {
      type: Object
    },
  }
}
</script>

<style>

</style>