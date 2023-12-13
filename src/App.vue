<template>
  <div>
    <!-- prevent it from reloading it -->
    <form @submit.prevent="sendInfo"
    >
    <!-- <form @submit="sendInfo"> this reloads the page -->
      <div>
        <label>Enter a Value</label>
        <input type="text" placeholder="Enter your value" v-model="currValue" @keyup.enter="popUpMessage(currValue)" >
        <!-- @keyup="popUpMessage(currValue)" -->
      </div>
      <div>
        <h3>List of entered values</h3>
        <ul v-show="listOfValues.length">
          <li v-for="data, index in listOfValues" :key="index">
            <p>{{ data }} @ position {{ index }}</p>
          </li>
        </ul>
      </div>
      <button type="submit" @click.prevent="sendInfo">Display</button>
    </form>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      currValue: '',
      listOfValues: []
    }
  },
  components: {},
  methods: {
    sendInfo(){
      if(this.currValue)
      this.listOfValues.push(this.currValue)
    },
    popUpMessage(arg){
      alert(arg)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
