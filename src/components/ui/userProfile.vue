<template>
  <div>
    <ul uk-accordion>
      <li class="profile uk-close" v-for="user in usersData" :key="user.id">
        <img class="user-img" :src="user.avatar" alt="" />
        <ul uk-accordion>
          <li class="uk-closed">
            <h2 class="uk-accordion-title"> {{ user.first_name + " " + user.last_name }}</h2>
            <div class="uk-accordion-content">
              <p>
                Job: {{ user.employment.title}}
              </p>
              <p>Phone: {{ user.phone_number }}</p>
              <p>Email: {{ user.email }}</p>
            </div>
          </li>
        </ul>
        
        <!-- <div class="tag-wrapper" v-for="tag in user.tags" :key="tag">
          <span class="tag">{{ tag }}</span>
        </div>
        <input
          class="tag-input"
          type="text"
          placeholder="Add a tag"
          v-model="tagInput"
          @keyup.enter="addTag(user)"
        /> -->
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "userProfile",
  props: {
    usersData: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      tagInput: "",
    };
  },

  methods: {
    addTag(user) {
      user.tags.push(this.tagInput);
      this.tagInput = "";
    },
  },
});
</script>

<style scoped>
.profile {
  padding: 50px 30px;
  margin: 30px 0;
  border-bottom: 1px solid #eee;
}

.uk-accordion-title {
  font-size: 1.5em;
}

.user-img {
  width: 120px;
  border: 1px solid;
  border-radius: 50%;
  margin-bottom: 30px;
}

/* .tag-wrapper {
  display: inline-block;
}

.tag {
  background-color: rgb(177, 177, 177);
  padding: 10px;
  margin: 5px;
  color: #fff;
}

.tag-input {
  display: block;
  margin-top: 4%;
  border: none;
  border-bottom: 1px solid gray;
  padding: 8px;
} */
</style>
