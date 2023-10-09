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
            <button class="scientific btn btn-primary">x²</button>
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
            <button class="scientific btn btn-primary">&#x003C0;</button>
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
padding: 0.5em 2em;
margin: 1em 1.5em;
border: none;
width: 15px;
height: 35px;
text-align: center;
background: #178;
color: white;
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
    width: 145px;
    background: #005f08;
}
</style>