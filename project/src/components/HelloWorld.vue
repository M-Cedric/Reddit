<template>
  <div class="hello">
<!--    <div v-for="proj in reddit">-->
<!--      <hi>{{ proj.title.rendered}}</hi>-->
<!--    </div>-->

    <div v-for="(title, proj) in reddit" :key="proj.id">
      {{proj}}. {{title.rendered}}
    </div>


  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    reddit: []
  },
  created: function () {
    this.$http.get('wp/v2/reddit').then(response => {
      for (let reddit in response.data){
        this.reddit.push(response.data[reddit]);
      }
    }, error => {
      alert(error);
    });
  }
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
/*a {*/
/*  color: #42b983;*/
/*}*/
</style>
