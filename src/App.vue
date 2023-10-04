<script>
  export default {
    data() {
      return {
        display: ''
      };
    },
    methods: {
      addToDisplay(value) {
        this.display += value;
      },
      clearDisplay() {
        this.display = '';
      },
      calculateResult() {
        try {
          this.display = this.display.replace(/sqrt/g, 'Math.sqrt');
          this.display = this.display.replace(/Math.sin/g, 'Math.sin');
          this.display = this.display.replace(/Math.cos/g, 'Math.cos');
          this.display = this.display.replace(/Math.tan/g, 'Math.tan');

          this.display = eval(this.display);
        } catch (error) {
          this.display = 'Error';
        }
      },
      deleteLastChar() {
        this.display = this.display.toString().slice(0, -1);
      }
    }
  }
</script>

<template>
  <div class="container">
      <div class="calculator">
          <form>
              <div class="display">
                  <input type="text" name="display" v-model="display" disabled>
              </div>
              <div>
                  <input type="button" value="AC" class="ac" @click="clearDisplay()">
                  <input type="button" class="del" value="Del" @click="deleteLastChar()">
                  <input type="button" class="symbols" value="." @click="addToDisplay('.')">
                  <input type="button" class="symbols" value="/" @click="addToDisplay('/')">
              </div>
              <div>
                  <input type="button" value="Sqrt" class="scientific"  @click="addToDisplay('sqrt(')">
                  <input type="button" class="scientific" value="Sin" @click="addToDisplay('Math.sin(')">
                  <input type="button" class="scientific" value="Cos" @click="addToDisplay('Math.cos(')">
                  <input type="button" class="scientific" value="Tan" @click="addToDisplay('Math.tan(')">
              </div>
              <div>
                  <input type="button" class="NumpadBtns" value="7" @click="addToDisplay('7')">
                  <input type="button" class="NumpadBtns" value="8" @click="addToDisplay('8')">
                  <input type="button" class="NumpadBtns" value="9" @click="addToDisplay('9')">
                  <input type="button" class="symbols" value="*" @click="addToDisplay('*')">
              </div>
              <div>
                  <input type="button" class="NumpadBtns" value="4" @click="addToDisplay('4')">
                  <input type="button" class="NumpadBtns" value="5" @click="addToDisplay('5')">
                  <input type="button" class="NumpadBtns" value="6" @click="addToDisplay('6')">
                  <input type="button" class="symbols" value="-" @click="addToDisplay('-')">
              </div>
              <div>
                  <input type="button" class="NumpadBtns" value="1" @click="addToDisplay('1')">
                  <input type="button" class="NumpadBtns" value="2" @click="addToDisplay('2')">
                  <input type="button" class="NumpadBtns" value="3" @click="addToDisplay('3')">
                  <input type="button" class="symbols" value="+" @click="addToDisplay('+')">
              </div>
              <div>
                  <input type="button" class="special" value="00" @click="addToDisplay('00')">
                  <input type="button" class="special" value="0" @click="addToDisplay('0')">
                  <input type="button" value="=" class="equal" @click="calculateResult()">
              </div>
          </form>
      </div>
  </div>
</template>

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
    Background: #e9e6ec;
    display:grid;
}
.container{
    width: 100%;
    
    height: 100%;

    display: flex;
}
.calculator{
    background: #4897eb;
    padding: 10px;
    box-shadow: 0px 0px 10px 3px rgba(0, 0, 0, 0.219);
    margin:auto;

    border-radius: 10px;
}

.calculator form input {
    border: 0;
    outline: 0;
    width: 60px;
    height:60px;
    border-radius: 10px;
    font-family: Nunito;
    font-weight: 700;
    font-size:1.7em;
    color: white;
    cursor: pointer;
    margin: 10px;

}
.calculator form input.NumpadBtns{
    background: #012a4a;
}
form .display{
    display: flex;
    justify-content: flex-end;
    margin: 20px 0;
}
form .display input{
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

form input.equal{
width: 145px;
background: #005f08
}
form input.ac,form input.del{
    background: #5f0000
}
.scientific {
    background-color:#47e732;
}

.symbols{
    background-color: #edae49;
}
.special{
    background: #248277;
}

.calculator form input:hover {
    box-shadow: 0px 0px 5px 3px #00000025;
}
</style>