<template>
  <div id="product-list">
    <p v-if="products.length == 0">Empty Product List</p>
    <table class="table">
      <thead>
        <tr>
          <th>Id</th>
          <th>Product Name</th>
          <th>Category</th>
          <th>Description</th>
          <th>Price</th>
          <th>Stock</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input
              v-model="product.id"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.id }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.productName"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.productName }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.categoryId"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.categoryId }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.quantityPerUnit"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.quantityPerUnit }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitPrice"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.unitPrice }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitsInStock"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.unitsInStock }}</td>

          <td v-if="updateId !== product.id">
            <button
              class="btn btn-sm btn-primary"
              @click="handleUpdate(product)"
            >
              UPDATE
            </button>
            <button
              class="btn btn-sm btn-danger"
              @click="handleDelete(product)"
            >
              X
            </button>
          </td>
          <td v-else>
            <button class="btn btn-sm btn-success" @click="handleSave(product)">
              Save
            </button>
            <button class="btn btn-sm btn-danger" @click="updateId = null">
              Cancel
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "product-list",
  data() {
    return {
      updateId: null,
    };
  },
  props: {
    products: Array,
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product) {
      this.$emit("update:product", product);
      this.updateId = null;
    },
  },
};
</script>

<style scoped>
#product-list {
  margin: 100px;
}
</style>
