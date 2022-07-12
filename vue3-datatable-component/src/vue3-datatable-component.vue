<template>
  <div class="container">
    <div class="vue-datatable-component p-3">
      <SearchComponent @setSearchQuery="setSearchQuery" v-if="searchFilter" />
    </div>
    <div class="vue-datatable-component-table my-2">
      <table id="tableComponent" class="table table-bordered table-striped">
        <thead>
          <tr>
            <!-- loop through each value of the fields to get the table header -->
            <th
              v-for="field in fields"
              :key="field"
              @click="sort ? sortTable(field) : ''"
              :title="`Sort by ${field}`"
            >
              {{ field }}

              <svg
                v-if="sort"
                xmlns="http://www.w3.org/2000/svg"
                class="h-1 w-1 ms-2"
                style="width: 20px"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="1"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4"
                />
              </svg>
            </th>
          </tr>
        </thead>
        <tbody v-if="filteredList.length > 0">
          <!-- Loop through the list get the each student data -->
          <tr v-for="item in filteredList" :key="item">
            <td v-for="field in fields" :key="field">{{ item[field] }}</td>
          </tr>
        </tbody>
        <tbody v-else>
          <tr>
            <td :colspan="fields.length" class="text-center">
              No results found
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import { sortBy } from "lodash";
import SearchComponent from "./SearchComponent.vue";
export default {
  name: "TableComponent",
  props: {
    //
    data: {
      type: Array,
      required: true,
    },
    fields: {
      type: Array,
      required: true,
    },
    searchFilter: {
      type: Boolean,
    },
    sort: {
      type: Boolean,
    },
  },

  components: {
    SearchComponent,
  },

  computed: {
    filteredList() {
      return this.updatedList.filter((product) => {
        for (const key in product) {
          if (
            product[key]
              .toLowerCase()
              .indexOf(this.searchQuery.toLowerCase()) != -1
          ) {
            return (
              product[key]
                .toLowerCase()
                .indexOf(this.searchQuery.toLowerCase()) != -1
            );
          } else {
          }
        }
      });
    },
  },

  data() {
    return {
      updatedList: [],
      searchQuery: "",
    };
  },
  methods: {
    sortTable(col) {
      // this.sort = true;
      // Use of _.sortBy() method
      this.updatedList = sortBy(this.data, col);
    },
    setSearchQuery(query) {
      query.length == 0 ? (this.searchQuery = "") : (this.searchQuery = query);
    },
  },

  created() {
    this.sortTable("ID");
  },
};
</script>

<style scoped>
@media (max-width: 768px) {
  .vue-datatable-component-table {
    width: 100%;
    overflow: scroll;
  }
}
</style>
