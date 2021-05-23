<template>
  <div class="hello">
<!--    <div :key="index" v-for="index in posts">Post-->
<!--    <h1>{{ posts.title}}</h1>-->
<!--    </div>-->
    <div :key="index" v-for="index in posts">Post
      <h1>{{ posts.id}}</h1>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
// const axios = require("axios");
// const { remote, ipcRenderer } = require("electron")
// const { Menu } = remote


export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    reddit: []
  },
  data() {
    return {
      posts: []
    }
  },
  created() {
    // this.initMenu();
    axios.get("http://localhost:8888/wordpress/wp-json/wp/v2/posts/")
        .then(response => {
          console.log(response)
          this.posts = response.data.data
        })
        .catch(error => {
          console.log(error)
        })
  },
  // methods: {
  //   initMenu() {
  //     const menu = Menu.buildFromTemplate([
  //       {
  //         label: "File",
  //         submenu: [
  //           { label: "New Window" },
  //           {
  //             label: "Settings",
  //             accelerator: "CmdOrCtrl+,",
  //             click: () => {
  //               ipcRenderer.send("toggle-settings");
  //             }
  //           },
  //           { type: "separator" },
  //           {
  //             label: "Quit",
  //             accelerator: "CmdOrCtrl+Q"
  //           }
  //         ]
  //       },
  //       {
  //         label: "Edit",
  //         submenu: [
  //           { label: "Menu Item 1" },
  //           { label: "Menu Item 2" },
  //           { label: "Menu Item 3" }
  //         ]
  //       }
  //     ]);
  //     Menu.setApplicationMenu(menu);
  //   },
  //   openImage(image) {
  //     ipcRenderer.send("toggle-image", image)
  //   }
  // }
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
.list-group {
  display: -ms-flexbox;
  display: flex;
  -ms-flex-direction: column;
  flex-direction: column;
  padding-left: 0;
  margin-bottom: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 0.75rem 1.25rem;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid rgba(0, 0, 0, 0.125);
}
.list-group-flush .list-group-item {
  border-right: 0;
  border-left: 0;
  border-radius: 0;
}
.list-group-flush:first-child .list-group-item:first-child {
  border-top: 0;
}
.flex-container {
  display: flex;
  align-items: center;
}
.thumbnail {
  width: 60px;
  height: 60px;
  border-radius: 30px;
  margin-right: 16px;
}
.list-group-item {
  cursor: pointer
}
.list-group-item:hover {
  background-color: #eee;
}

/*a {*/
/*  color: #42b983;*/
/*}*/
</style>
