<template>
  <h1>Api Call</h1>
</template>

<script>
import axios from "axios";
export default {
  name: "CallApi",
  created() {
    axios
      .get("https://api.github.com/users")
      .then((response) => {
        this.user = response.data;
        console.log(response);
        console.log(this.user);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped></style>
