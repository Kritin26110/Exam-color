<template>
  <div class="hello">
    <div v-for="(d,index) in Info" :key="index">
      <center>
        <b-card class="container">
          
          <p class="card-text">{{d.color}}</p>
          <p class="card-text">{{d.category}}</p>
          <p class="card-text">{{d.code}}</p>
          <p class="card-text">{{d.type}}</p>
        </b-card>
      </center>
      <br>
    </div>
    
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      Info: []
    };
  },
  mounted() {
    axios.get("https://cs494-5-cc968.firebaseio.com/colors.json").then(response => {
      const data = response.data;
      for (let key in data) {
        const info = data[key];
        info.id = key;
        this.Info.push(info);
      }
    });
  }
};
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
a {
  color: #42b983;
}
</style>
