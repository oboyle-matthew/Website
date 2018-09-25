<template>
  <div v-bind:style="flex" id="app">
    <div v-bind:style="dateStyle">
      <p>{{date}}</p>
    </div>
    <div v-bind:style="infoStyle">
      <h3>{{position}}</h3>
      <h5>{{title}}</h5>
      <p>{{info}}</p>

    </div>

  </div>
</template>

<script>
  export default {
    name: 'app',
    props: ['date', 'info', 'title', 'position'],
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        flex: {
          display: 'flex',
          flexDirection: 'row',
          marginLeft: '5vw',
          marginRight: '5vw',
          marginTop: '5vh',
          marginBottom: '5vh'
        },
        dateStyle: {
          position: 'relative',
          // backgroundColor: 'grey',
          width: '30vw',
          fontSize: '2vw'
        },
        infoStyle: {
          // backgroundColor: 'red',
          width: '60vw'
        }
      }
    }
  }
</script>
