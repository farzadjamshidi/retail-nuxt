<template>
  <div class="product-container">
    <div
      class="product-image"
      v-bind:style="{
        backgroundImage: 'url(' + product.imageURL + ')',
      }"
    ></div>
    <div class="product-other-info">
      <span class="product-name">{{ product.name }}</span>
      <span class="product-description">{{ product.description }}</span>
    </div>
    <span class="product-price">${{ product.price }}</span>
    <div class="add-to-cart-button-container">
      <div class="add-to-cart-button">
        <span>Add to cart</span>
        <span class="shopping-cart-icon">
          <font-awesome-icon :icon="['fas', 'shopping-cart']" />
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      required: true,
      type: Object,
    },
  },
};
</script>

<style scoped>
.product-container {
  padding: 10px;
  border: 1px solid #bdb9b9;
  width: 250px;
  height: 350px;
}
.product-image {
  background-size: cover;
  height: 180px;
}
.product-other-info {
  display: flex;
  flex-direction: column;
  margin: 15px 0px;
}
.product-name {
  font-size: 18px;
  color: #a8c6e0;
  display: inline-block;
}
.product-description {
  color: #d8d8d8;
  display: inline-block;
}
.product-price {
  display: inline-block;
  margin-bottom: 10px;
}
.add-to-cart-button-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.add-to-cart-button {
  width: 150px;
  border: 1px solid;
  padding: 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.shopping-cart-icon {
  display: inline-block;
  margin-left: 5px;
}
</style>
