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
            <option>cat1</option>
            <option>cat2</option>
            <option>cat3</option>
          </select>
        </div>
      </div>
    </div>
    <div class="content"></div>
  </div>
</template>

<script>
export default {
  layout: "default",
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
}
</style>
