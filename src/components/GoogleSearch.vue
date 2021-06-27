<template>
  <form>
    <div class="container col-sm-5 mb-3">
      <input
        class="form-control"
        type="text"
        placeholder="enter your keyword"
        aria-label="default input example"
        v-model="keyword"
      />
    </div>
    <div class="mb-3">
      <button type="button" class="btn btn-light" @click="search">
        Google search
      </button>
      <button type="button" class="btn btn-light">I'm Feeling Lucky</button>
    </div>

    <div class="list-group">
      <ul class="list-group">
        <li
          class="list-group-item"
          aria-current="true"
          v-for="item in Response"
          :key="item.title"
        >
          <p class="link">{{ item.link }}</p>
          <a :href="item.link" class="titlelink">{{ item.title }}</a>
          <p class="description">{{ item.snippet }}</p>
        </li>
      </ul>
    </div>
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      keyword: "",
      Response: [],
      apikey: "",
      cx: "",
    };
  },
  methods: {
    async search(e) {
      e.preventDefault();
      const response = await axios.get(
        `https://www.googleapis.com/customsearch/v1?key=${this.apikey}&cx=${this.cx}&q=${this.keyword}`
      );
      this.Response = response.data.items;

      //this.Response = response.data;
      console.log(response.data.items);
    },
  },
};
</script>

<style>
.link {
  color: #202124;
  font-size: 14px;
  font-style: normal;
  text-align: left;
  margin-bottom: 3px;
  padding: 0px;
}
.description {
  color: #202124;
  text-align: left;
  line-height: 1.58;
  max-width: 48em;
  margin: 0px;
}
.titlelink {
  margin: 0px;
  text-align: left;
}
</style>
