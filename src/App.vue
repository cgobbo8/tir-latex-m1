<template>
  <div>
    <Article class="article" v-for="item in items" :key="item.data.key" v-show="item.data.itemType != 'note'" :item="item" ></Article>
    
  </div>
</template>

<script>
import Article from "./components/Article.vue";
import axios from "axios";

export default {
  components : {
    Article
  },
  data() {
    return {
      items: [],
    };
  },
  async mounted() {
    let response = await axios.get(
      "https://api.zotero.org/users/7549136/items"
    );
    this.items = response.data;
    console.log(response.data);
  },
};
</script>

<style lang="scss" >
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}


</style>