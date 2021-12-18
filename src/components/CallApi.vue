<template>
  <h1>Github Api Call</h1>
  <div class="chunck_display">
    <table>
      <tr class="chunck_topics">
        <td>Name</td>
        <td>Node id</td>
        <td>Type</td>
        <td>Followers_Url</td>
        <td>Following_Url</td>
      </tr>
      <tr v-for="item in list" v-bind:key="item.id">
        <td>{{ item.login }}</td>
        <td>{{ item.node_id }}</td>
        <td>{{ item.type }}</td>
        <td>{{ item.followers_url }}</td>
        <td>{{ item.following_url }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CallApi",
  data() {
    return {
      list: [],
    };
  },
  created() {
    axios
      .get("https://api.github.com/users")
      .then((response) => {
        this.user = response.data;
        this.list = response.data;
        console.log(response);
        if (response.status == 200) {
          alert("success " + response.status);
        } else {
          alert("error " + response.status);
        }
        console.log(this.user);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
.chunck_display {
  display: flex;
  justify-content: center;
}
table {
  border: 3px solid greenyellow;
}
td {
  border: 2px solid orange;
  padding: 0 10px 0 10px;
  font-size: 14px;
}
.chunck_topics {
  font-weight: bold;
}
</style>
