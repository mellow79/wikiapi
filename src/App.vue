<template>
    <div class="container">
      <Header   title="Consume Wiki API"/>
      <Wikis :wikis="wikis"></Wikis>
    </div>
</template>

<script>
import Header from './components/Header'
import Wikis from './components/Wikis'

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

// Import Bootstrap an BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(VueAxios, axios)
// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)


export default {
  name: 'App',
  components: {
    Header,
    Wikis
  },
  data: function(){
    return {
      wikis: Object,
      new_array : Array
    }
  },
  methods: {
    // Get all wikis
    getWikis: function () {
      axios.get('https://en.wikipedia.org/w/rest.php/v1/search/title?q=Foo&limit=10',).then((response) => {

        this.wikis = response.data.pages;

        // using the spread operator allows us to add to the end of array of objects
        this.wikis = [...this.wikis,{"text":"Search for pages containing [x]"}]


        return this.wikis;
      })
          .catch((err) => {
            console.log("AXIOS ERROR: ", err);
          })
    }
  },
  created(){
    this.wikis = this.getWikis();
  }
}
</script>

<style>

</style>
