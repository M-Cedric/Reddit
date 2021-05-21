<template>
  <div class="hello">

    <div class="button">
      <md-button v-for="item in post" :key="item.data.id" onclick="created">Default</md-button>
    </div>

  </div>
</template>

<script>
const axios = require("axios");


export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    reddit: []
  },
  data() {
    return {
      post: []
    }
  },
  created() {
    // this.initMenu();
    axios.get("http://localhost:8888/wordpress/wp-json/wp/v2/posts/")
        .then(response => {
        console.log(response)
        })
        .catch(error => {
          console.log(error)
        })
  },
  // created: function () {
  //   this.$http.get('wp/v2/reddit').then(response => {
  //     for (let reddit in response.data){
  //       this.reddit.push(response.data[reddit]);
  //     }
  //   }, error => {
  //     alert(error);
  //   });
  // }
}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
button {
  background: black;
}
/*a {*/
/*  color: #42b983;*/
/*}*/
</style>
