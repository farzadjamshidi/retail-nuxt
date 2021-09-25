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
      <div
        class="add-to-cart-button"
        v-if="shoppingCart.count === 0"
        @click="addToCart"
      >
        <span>Add to cart</span>
        <span class="shopping-cart-icon">
          <font-awesome-icon :icon="['fas', 'shopping-cart']" />
        </span>
      </div>
      <div class="add-to-cart-button" v-if="shoppingCart.count !== 0">
        <span class="increase-icon" @click="increase">
          <font-awesome-icon :icon="['fas', 'plus-circle']" />
        </span>
        <span class="product-count">{{ shoppingCart.count }}</span>
        <span class="decrease-icon" @click="decrease">
          <font-awesome-icon :icon="['fas', 'minus-circle']" />
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
    shoppingCartOfProduct: {
      required: true,
      type: Object,
    },
  },
  data() {
    return {
      shoppingCart: this.shoppingCartOfProduct,
    };
  },
  methods: {
    addToCart() {
      this.$emit("increase", this.product);
    },
    increase() {
      this.$emit("increase", this.product);
    },
    decrease() {
      this.$emit("decrease", this.product);
    },
  },
  watch: {
    shoppingCartOfProduct: function (
      newShoppingCartOfProduct,
      oldShoppingCartOfProduct
    ) {
      this.shoppingCart = newShoppingCartOfProduct;
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
.product-count {
  display: inline-block;
  margin: 0px 15px;
}
.increase-icon {
}
.decrease-icon {
}
</style>
