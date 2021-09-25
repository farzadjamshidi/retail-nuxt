<template>
  <div class="page-container">
    <div class="header">
      <div class="header-info">
        <span>Company Name</span>
        <div class="shopping-cart-details">
          <span>30 items added</span>
          <div class="shopping-cart-total">
            <span>$30</span>
            <span class="shopping-cart-icon">
              <font-awesome-icon :icon="['fas', 'shopping-cart']" />
            </span>
          </div>
        </div>
      </div>
      <div class="categories">
        <div class="categories-info">
          <span>You're browsing</span>
          <select class="select-category">
            <option v-for="category in categories" :key="category.id">
              {{ category.name }}
            </option>
          </select>
        </div>
      </div>
    </div>
    <div class="content">
      <Product
        class="pruduct"
        v-for="product in products"
        :key="product.id"
        :product="product"
        :shoppingCartOfProduct="shoppingCartOfProduct(product)"
      />
    </div>
  </div>
</template>

<script>
import Product from "../components/Product.vue";
import products from "../products-mock-data";

export default {
  components: { Product },
  layout: "default",
  data() {
    return {
      products: [],
      categories: [],
      shoppingCart: {},
    };
  },
  mounted() {
    this.products = products;
    this.categories = products.reduce((acc, product) => {
      if (acc && !acc.some((category) => category.id === product.category.id))
        acc.push(product.category);

      return acc;
    }, []);

    this.categories.forEach((category) => {
      this.shoppingCart[category.id] = {
        itemCount: 0,
        totalPrice: 0,
        products: {
          // 'poroductID' : {count : 0}
        },
      };
    });
  },
  computed: {
    shoppingCartOfProduct: function () {
      return (product) =>
        this.shoppingCart[product.category.id]["products"][product.id] || {
          count: 0,
        };
    },
  },
};
</script>

<style scoped>
.page-container {
}

.header {
  height: 80px;
  display: flex;
  flex-direction: column;
  border: 1px solid #bdb9b9;
}

.header-info {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: #575757;
  color: rgba(245, 245, 245, 0.863);
  padding: 10px;
}

.shopping-cart-details {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 180px;
}

.shopping-cart-total {
}
.shopping-cart-icon {
}

.categories {
  display: flex;
  flex-direction: row-reverse;
  padding: 10px;
}
.categories-info {
  display: flex;
  flex-direction: row;
}
.select-category {
  margin-left: 10px;
}

.content {
  height: calc(100vh - 80px);
  padding: 40px 100px;
  display: flex;
  flex-wrap: wrap;
  overflow-y: scroll;
}
.content .pruduct {
  margin: 10px;
}
</style>
