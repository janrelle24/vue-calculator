<template>
    <div @click="buttonClick">
        <div>
            <button class="scientific btn btn-primary">sin</button>
            <button class="scientific btn btn-primary">cos</button>
            <button class="scientific btn btn-primary">tan</button>
            <button class="scientific btn btn-primary">x^</button>
            <button class="scientific btn btn-primary">&larr;</button>
            <button class="scientific btn btn-primary">C</button>
        </div>
        <div>
            <button class="scientific btn btn-primary">log</button>
            <button class="scientific btn btn-primary">ln</button>
            <button class="scientific btn btn-primary">e</button>
            <button class="scientific btn btn-primary">∘</button>
            <button class="scientific btn btn-primary">rad</button>
            <button class="scientific btn btn-primary">√</button>
        </div>
        <div>
            <button class="numpad btn btn-primary">7</button>
            <button class="numpad btn btn-primary">8</button>
            <button class="numpad btn btn-primary">9</button>
            <button class="symbols btn btn-primary">/</button>
            <button class="scientific btn btn-primary">&#x003C0;</button>
            <button class="scientific btn btn-primary">x!</button>
        </div>
        <div>
            <button class="numpad btn btn-primary">4</button>
            <button class="numpad btn btn-primary">5</button>
            <button class="numpad btn btn-primary">6</button>
            <button class="symbols btn btn-primary">*</button>
            <button class="ac btn btn-primary">(</button>
            <button class="ac btn btn-primary">)</button>
        </div>
        <div>
            <button class="numpad btn btn-primary">1</button>
            <button class="numpad btn btn-primary">2</button>
            <button class="numpad btn btn-primary">3</button>
            <button class="symbols btn btn-primary">-</button>
            <button class="symbols btn btn-primary">%</button>
            <button class="symbols btn btn-primary">+</button>
        </div>
        <div>
            <button class="symbols btn btn-primary">±</button>
            <button class="numpad btn btn-primary">0</button>
            <button class="symbols btn btn-primary">.</button>
            <button class="symbols btn btn-primary">+</button>
            <button class="equal btn btn-primary">=</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Scientific',
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
.numpad{
    background: #012a4a;
}
.symbols{
    background-color: #edae49;
}
.ac{
    background: #5f0000;
}
.scientific{
    background-color:#47e732;
}
.equal{
    width: 200px;
    background: #005f08;
}

</style>