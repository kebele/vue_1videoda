<template>
  <div class="product">
    <strong>{{ product.title }}</strong>
    <p>{{ product.description }}</p>
    <strong>fiyat : {{ product.price }} | adet : {{ product.count }}</strong>
    <br><br>
    <button>sepete ekle</button>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style>
.product {
  border: 2px dashed #666;
  padding: 5px 10px;
  width: 300px;
  margin-bottom: 5px;
}
.product:hover {
  border: 2px solid #666;
  transition: all 0.5s;
}
</style>
