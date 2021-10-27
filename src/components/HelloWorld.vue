<template>
  <div class="hello"  >
    <div class="col-md-12" v-for="item in list.data" v-bind:key="item.id">
      <div class="row">
        
        <div class="col-md-2">
           {{item.id}}
        </div>
        <div class="col-md-2">  
          {{item.first_name}}
        </div>
          <div class="col-md-2">
         {{item.last_name}}
          </div>
          <div class="col-md-2">
        {{item.email}}
          </div>
        <div class="col-md-2">
          <img :src="(item.avatar)">
         
        </div>
        <div class="col-md-2" v-if="item!=null">
          <button class="btn-primary" v-on:click="deletedatalist(item.id)"> Delete </button>
         
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import axios from 'axios'


export default {
  data:()=>({
    list:'',
  }),
  name: 'HelloWorld',
  
  created() {
    
  },
  mounted(){
   axios.get("https://reqres.in/api/users")
    .then((result) => {this.list = result.data;
    })
  },
  method:{
    

    deletedatalist(item){
     axios.delete("https://reqres.in/api/users/" +item)
          .then(( ) => {this.getdata();
    })
      
    }
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
a {
  color: #42b983;
}
</style>
