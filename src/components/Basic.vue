<template>
    <div @click="buttonClick">
        <div>
            <button class="numpad btn btn-primary">7</button>
            <button class="numpad btn btn-primary">8</button>
            <button class="numpad btn btn-primary">9</button>
            <button class="symbols btn btn-primary">/</button>
            <button class="ac btn btn-primary">&larr;</button>
            <button class="ac btn btn-primary">C</button>
        </div>
        <div>
            <button class="numpad btn btn-primary">4</button>
            <button class="numpad btn btn-primary">5</button>
            <button class="numpad btn btn-primary">6</button>
            <button class="symbols btn btn-primary">*</button>
            <button class="ac btn btn-primary"> ( </button>
            <button class="ac btn btn-primary"> ) </button>
        </div>
        <div>
            <button class="numpad btn btn-primary">1</button>
            <button class="numpad btn btn-primary">2</button>
            <button class="numpad btn btn-primary">3</button>
            <button class="symbols btn btn-primary">-</button>
            <button class="symbols btn btn-primary">x²</button>
            <button class="symbols btn btn-primary">±</button>
        </div>
        <div>
            <button class="numpad btn btn-primary">0</button>
            <button class="symbols btn btn-primary">.</button>
            <button class="symbols btn btn-primary">%</button>
            <button class="symbols btn btn-primary">+</button>
            <button class="equal btn btn-primary">=</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Basic',
    data () {
        return {

        }
    },
    methods: {

        buttonClick: function(e){
            let value = e.target.innerHTML;
            this.$emit('addNumber', value) 
        }
    }
}
</script>

<style>
button {
    /*
padding: 0.5em 2em;
margin: 1em 1.5em;
border: none;
width: 15px;
height: 35px;
text-align: center;
background: #178;
cursor: pointer;
color: white;*/
border: 0;
outline: 0;
width: 100px;
height:100px;
border-radius: 20px;
font-family: Nunito;
font-weight: 400;
font-size:1.7em;
color: white;
cursor: pointer;
margin: 10px;
}
button:hover{
    box-shadow: 0px 0px 5px 3px #00000025;
}
.numpad{
    background: #012a4a;
}
.symbols{
    background-color: #edae49;
}
.ac{
    background: #5f0000;
}
.equal{
    width: 200px;
    background: #005f08;
}

</style>