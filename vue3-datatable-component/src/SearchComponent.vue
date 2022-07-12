<template>
  <div class="vue-datatable-component-search-box ms-auto">
    <!-- Filter Search -->
    <div class="input-group mb-2">
      <input
        type="search"
        class="form-control"
        v-model="searchQuery"
        placeholder="Search"
        aria-label="Search"
        aria-describedby="button-addon2"
        @keyup="emitFilterData"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
    };
  },
  methods: {
    emitFilterData() {
      this.$emit("setSearchQuery", this.searchQuery.trim());
    },
  },
};
</script>

<style scoped>
@media (min-width: 768px) {
  .vue-datatable-component-search-box {
    width: 40%;
  }
}
</style>
