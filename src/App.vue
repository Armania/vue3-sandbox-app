<template>
  <div id="app">
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view />
    <h1>Hello Kendo UI for Vue!</h1>
    <p>
      <dropdownlist
        :data-items="categories"
        :data-item-key="'CategoryID'"
        :text-field="'CategoryName'"
        :default-item="defaultItems"
        @change="handleDropDownChange"
      ></dropdownlist>&nbsp; Selected category ID:
      <strong>{{ dropdownlistCategory }}</strong>
    </p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { categories } from './appdata/categories';
import { DropDownList } from '@progress/kendo-vue-dropdowns';
import '@progress/kendo-theme-default/dist/all.css';

export default defineComponent({
  name: 'App',
  components: {
    'dropdownlist': DropDownList,
  },
  data: function() {
    return {
      categories: categories,
      defaultItems: {CategoryID: null, CategoryName: "Product categories"},
      dropdownlistCategory: null
     }
  },
  methods: {
      handleDropDownChange(e: DropDownListChangeEvent) {
        this.dropdownlistCategory = e.target.value.CategoryID;
      }
  }
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
