<template>
<div id="this">

  <div class="container">
    <div class="calculator">
      <p> {{ mode }} </p>   
      <div class="row input-data">
        <div class="col-lg-12">
          <div class="input-group">
            <span class="input-group-addon"> <input class="input-data" @click="changeToggle" type="checkbox" aria-label="Checkbox for following text input"> </span>
            <input type="text" class="form-control text-right" v-model="current" aria-label="Text input with checkbox" disabled>
          </div>
        </div>
      </div>

      <hr>

      <div class="buttons">

        <Basic v-show="!toggle" v-bind:current="current" @addNumber="doStuff($event)"></Basic>
        <Scientific v-show="toggle"  v-bind:current="current" @addNumber="doStuff($event)"></Scientific>

      </div>
    </div>
  </div>

</div>
</template>

<script>
import Basic from './components/Basic';
import Scientific from './components/Scientific';

export default{
  name: 'Calculator',
  components: {
    'Basic' : Basic,
    'Scientific' : Scientific
    
  },
  data () {
    return {
      current: 0,
      toggle: false,
      mode: 'Basic'
    }
  },
  methods: {
    changeToggle: function() {
      this.toggle = !this.toggle;
      if(this.mode == 'Basic') {
        this.mode = 'Scientific' 
      }else{
        this.mode = 'Basic'
      }
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@200;300;400;500;600;700;800;900;1000&display=swap');
*{
    margin: 0px;
    padding:0px;
    font-family: Arial, Helvetica, sans-serif;
    box-sizing: border-box;
    user-select: none;
}
body{ /**new add */
    height:100vh;
    Background: #8608ee;
    display:grid;
}

.container{
  
  height: 35em;
  width: 55%;
  margin: 5% auto;
  border: 5px solid rgb(95, 233, 169);
  border-radius: 15px;
  
  /*
  height: 35em;
  width: 55%;
  margin: 5% auto;
  border-radius: 15px;
  border: 5px solid grey; */
}
.calculator{
    background: #023e7d;
    padding: 10px;
    box-shadow: 0px 0px 10px 3px rgba(0, 0, 0, 0.219);
    margin:auto;
    border-radius: 10px;
}

.input-group {
  display: flex;
  justify-content: center;
}

.text-right{
 /* 
font-size : 2em;
color: red; */
text-align: right;
flex: 2;
font-size: 45px;
box-shadow: none;
padding:20px;
box-sizing: border-box;
background: #218380; 
box-shadow: 0 0 10px 3px #00000033;
height:80px;
color: white;
}

.input-data{
  padding: 0em 0.5em;
  height: 2em;
} 

hr { 
    display: block;
    margin-top: 3em;
    margin-bottom: 0.5em;
    margin-left: auto;
    margin-right: auto;
    border-style: inset;
    border-width: 1px;
}

p {
  color: white;
  text-align: center;
  font-size: 1.5em;
  padding: 0.2em 0px;
}
</style>