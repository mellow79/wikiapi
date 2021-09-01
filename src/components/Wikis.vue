<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12 col-sm-12 col-xs-12">
        <ul class="row list-unstyled" v-on:load="sortKey = orderBy">
          <li v-for='wiki in wikis'
              :key='wiki.id' >
            <div class="row">
              <div class="col-md-2" v-if="wiki.thumbnail" >
                <img class="img-thumbnail img-responsive" :src="wiki.thumbnail.url" />
              </div>
              <div class="col-md-2" v-else>
                <!-- You can add a placeholder image here -->
              </div>
              <div class="col-md-10" >
                <h3>{{ wiki.title }}</h3>
                <p>{{ wiki.description}}</p>
              </div>
              <div class="col-md-12" v-if="wiki.text">
                <p>{{ wiki.text}}</p>
              </div>
              <hr />
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Wikis",
  props:{
    wikis: Array
  },
  methods: {

  },
}

</script>

<style scoped>
img{
  width: 100px;
  height: 100px;
}
hr{
  margin-top: 10px;
}
.asc:after{
  content: "\25B2"
}

.desc:after{
  content: "\25BC"
}
</style>