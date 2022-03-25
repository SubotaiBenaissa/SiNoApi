<template>
    <h2>{{customTitle}} {{start}}</h2>
    <p>{{ counter }} <sup>2</sup> = {{contadorCuadrado}}</p>

    <div>
        <button @click="incrementar">+1</button>
        <button @click="decrementar">-1</button>
    </div>
</template>

<script>

export default {

    props: {
        titulo: String,
        start: {
            type: Number,
            default: 1,
            required: true,
            validator(value) {
                return value >= 100
            }
        },
    },

    data() {
        return {
            counter: this.start
        }
    },

    methods: {
        valorCuadrado() {
            return this.counter * this.counter
        },

        incrementar() {
            this.counter++
        }, 

        decrementar() {
            this.counter--
        },
    },

    computed: {
        contadorCuadrado() {
            return this.counter * this.counter
        },
        customTitle() {
            return this.titulo || 'Counter'
            /*if (this.titulo == undefined) {
                titulo = 'Counter'
            }
            return this.titulo*/
        }
    } 
}

</script>

<style>

    button {
        background-color: #64BB87;
        border-radius: 5px;
        border: 1px solid white;
        color: white;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;
    }

    button:hover {
        background-color: #5aa67b;
        transition: 0.3s;
    }

</style>