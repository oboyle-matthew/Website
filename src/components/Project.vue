<template>
  <div v-bind:style="appStyle">
    <img class="col-lg-8 project_image" :src="require(`../assets/${image}`)">
    <div class="col-lg-3">
      <h3>{{name}}</h3>
      <p id="project_text">{{info}}</p>
      <a v-bind:href="demo" target="_blank">View</a>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'app',
    props: ['name', 'info', 'image', 'demo'],
    data () {
      return {
        appStyle: {
          display: 'flex',
          flexDirection: 'row',
          marginTop: '5vh',
          marginBottom: '3vh',
          width: '45vw'
        }
      }
    }
  }
</script>

<style>

  #project_text {
    font-size: 15px;
  }

  .project_image {
    width: 50vw;
    height: 50vh;
  }
</style>
