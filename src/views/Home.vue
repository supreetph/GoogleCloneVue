<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/googlelogo.png" />
    <GoogleSearch />
  </div>
</template>

<script>
// @ is an alias to /src
import GoogleSearch from "../components/GoogleSearch.vue";
//import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    GoogleSearch,
  },
};
</script>
