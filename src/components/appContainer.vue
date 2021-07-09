<template>
  <div class="container">
    <input
      class="search-bar"
      type="text"
      placeholder="search by name - Case Sensitive"
      v-model="search"
    />
    <userProfile :usersData="filteredList || tagsFilter"></userProfile>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
import userProfile from "./ui/userProfile.vue";
export default Vue.extend({
  name: "app-container",

  components: {
    userProfile,
  },

  data() {
    return {
      search: "",
      searchTag: "",
      usersData: [],
    };
  },

  computed: {
    filteredList() {
      return this.usersData.filter((user) => {
        return (
          user.first_name.includes(this.search) ||
          user.last_name.includes(this.search)
        );
      });
    },

    // tagsFilter() {
    //   return this.usersData.filter((user) => {
    //     return user.tags.includes(this.searchTag);
    //   });
    // },
  },
  async created() {
    // fetch data from api
    try {
      let { data } = await axios.get(
        "https://random-data-api.com/api/users/random_user?size=12"
      );
      data.forEach((element) => {
        element.tags = [];
      });
      console.log(data);
      this.usersData = data;
    } catch (err) {
      console.log(err);
    }
  },
});
</script>

<style scoped>
.container {
  width: 990px;
  padding: 20px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 4px 1px 15px -5px rgba(0, 0, 0, 0.62);
  background-color: #fff;
  height: 95vh;
  margin-top: 30px;
  overflow: scroll;
}
input:focus {
  outline: none;
  border-bottom-color: tomato;
}

::placeholder {
  opacity: 0.7;
}
.search-bar {
  width: 95%;
  padding: 15px;
  margin: 0 15px;
  border: none;
  border-bottom: 3px solid #eee;
  font-size: 1.5em;
  color: rgb(31, 31, 31);
}
</style>