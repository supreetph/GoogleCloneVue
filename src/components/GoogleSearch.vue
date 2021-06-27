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
      this.Response = response.data;

      //this.Response = response.data;
      console.log(response.data);
    },
  },
};
</script>

<style></style>
