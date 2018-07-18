<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
        <button @click="getTest(1)">点击一次</button>
        <button @click="getTest(2)">点击2次</button>
        <button @click="getTest(3)">点击3次</button>
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios'
  axios.defaults.withCredentials = true
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted(){
    // this.getTest()
  },
  myOption:'111',
  methods:{
    getTest(val){
      console.log(this.$options.myOption)//111
      if(val == 1){
        var param  = null
      }else if(val == 2){
        var param = {'ticket':'1111'}
      }else{
        var param = null
      }
      alert(param)
      // axios({
      //     method: 'GET',
      //     url: 'http://172.16.5.232:8080/healthmanage/appVersion/test',
      //     headers: {
      //       'Content-Type': 'application/json; charset=UTF-8',
      //     }
      //   }).then(res => {
      //     // this.callback(res)
      //   }).catch(res => {
      //     // this.error(res)
      //   })
      axios.get('http://172.16.5.232:8080/healthmanage/appVersion/appVersions',{params:param,'xhrFields': {'withCredentials': true}})
      .then(function(response){
        console.log(response);
      })
      .catch(function(err){
        console.log(err);
      });
      // this.$ajax.get('http://172.16.5.232:8080/healthmanage/appVersion/test',{params:null})
      //   .then(function (response) {
      //   console.log(response);
      //   })
      //   .catch(function (error) {
      //   console.log(error);
      //   });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
