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

        <Basic v-show="!toggle" v-bind:current="current" @addNumber="doCalculation($event)"></Basic>
        <Scientific v-show="toggle"  v-bind:current="current" @addNumber="doCalculation($event)"></Scientific>

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
    },
    doCalculation: function(data) {
      let temp;
      if(Number(data) || data ==0){
        temp =data
        if(this.current === 0 ) this.current = "";
        this.current+= "" + temp;
      }
      if(!Number(data)) {
        console.log(data);

        switch(data) {
          
          case "/": {
            this.divide();
            break;
          }
          case "←": {
            this.backspace();
            break;
          }
          case "C": {
            this.clear();
            break;
          }
          case "*": {
            this.multiply();
            break;
          }
          case "-": {
            this.minus();
            break;
          }
          case "+": {
            this.plus();
            break;
          }
          case "x²": {
            this.square();
            break;
          }
          case "(": {
            this.openbracket();
            break;
          }
          case ")": {
            this.closebracket();
            break;
          }
          case "=": {
            this.equals();
            break;
          }
          case "±": {
            this.plusMinus();
            break;
          }
          case "%": {
            this.percent();
            break;
          }
          case ".": {
            this.decimal();
            break;
          }
          case "sin": {
            this.sin();
            break;
          }
          case "cos": {
            this.cos();
            break;
          }
          case "tan": {
            this.tan();
            break;
          }
          case "ln": {
            this.ln();
            break;
          }
          case "e": {
            this.exp();
            break;
          }
          case "∘": {
            this.degrees();
            break;
          }
          case "x!": {
            this.factorial();
            break;
          }
          case "rad": {
            this.radians();
            break;
          }
          case "√": {
            this.squareRoot();
            break;
          }
          case "x^": {
            this.exponent();
            break;
          }
          case "π": {
            this.pi();
            break;
          }
          case "log": {
            this.log();
            break;
          }
        }
      }
    },
    divide: function(){
      this.current += "/";
    },
    backspace: function(){
      /*this.current = this.current.substring(0, this.current.length - 1);*/
      this.current = this.current.toString().slice(0,-1);
    },
    multiply: function(){
      this.current += "*";
    },
    clear: function() {
      this.current = 0;
    },
    minus: function(){
      this.current += "-";
    },
    plus: function(){
      this.current += "+";
    },
    square: function(){
      this.current = (this.current * this.current);
    },
    openbracket: function(){
      this.current += "(";
    },
    closebracket: function(){
      this.current += ")";
    },
    equals: function(){
      if ((this.current).indexOf("^") > -1) {
        var base = (this.current).slice(0, (this.current).indexOf("^"));
        var exponent = (this.current).slice((this.current).indexOf("^") + 1);
        this.current = eval("Math.pow(" + base + "," + exponent + ")");
        
      } else {
      this.current = eval(this.current);
      }
    },
    plusMinus: function() {
      if ( (this.current !== 0) && this.current.charAt(0) === "-" )  {
        this.current = this.current.slice(1);
      } else {
        this.current = "-" + this.current;
      }
    },
    percent: function(){
      this.current = this.current / 100 ;
    },
    decimal: function(){
      this.current += ".";
    },
    sin: function(){
      this.current = Math.sin(this.current);
    },
    cos: function(){
      this.current = Math.cos(this.current);
    },
    tan: function(){
      this.current = Math.tan(this.current);
    },
    ln: function(){
      this.current = Math.log(this.current);
    },
    exp: function(){
      this.current = Math.exp(this.current);
    },
    degrees: function(){
      this.current = this.current * (180 / Math.PI);
    },
    factorial: function () {
      var number = 1;
      if (this.current === 0) {
        this.current = "1";
      } else if (this.current < 0) {
        this.current = NaN;
      } else {
        var number = 1;
        for (var i = this.current; i > 0; i--) {
          number *=  i;
        }
        this.current = number;
      }
    },
    radians: function (){
      this.current = this.current * (Math.PI * 180);
    },
    squareRoot: function(){
      this.current = Math.sqrt(this.current);
    },
    exponent: function () {
      this.current += "^";
    },
    pi: function() {
      this.current = (this.current * Math.PI);
    },
    log: function () {
      this.current = Math.log10(this.current);
    },
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
body{ 
    height:100vh;
    Background: #8608ee;
    display:grid;
}

.container{
  
  height: 35em;
  width: 55%;
  margin: 5% auto;
  /*border: 5px solid rgb(95, 233, 169);*/
  border-radius: 15px;
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
text-align: right;
flex: 2;
font-size: 45px;
box-shadow: none;
padding:20px;
box-sizing: border-box;
background: #218380; 
box-shadow: 0 0 10px 3px #00000033;
height:80px;
border-radius: 10px;
cursor: pointer;
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