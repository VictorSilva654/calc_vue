<script setup>
import { reactive } from 'vue';

const estado = reactive({
    valor1: 0,
    valor2: 0,
    resultado: 0,
    filtragemContas: filtro => {
        switch(filtro) {
        case "adicao":
            estado.resultado = parseFloat(estado.valor1) + parseFloat(estado.valor2)
            return estado.resultado
        case "subtracao":
            estado.resultado = estado.valor1 - estado.valor2
            return estado.resultado
        case "multiplicacao":
            estado.resultado = estado.valor1 * estado.valor2
            return estado.resultado
        default:
            estado.resultado = estado.valor1 / estado.valor2
            return estado.resultado
        }
    }
})

</script>

<template>
    <div class="container">
        <h1 class="mt-5 mb-5 text-center display-1">Calculadora VueJS</h1>
        <form>
            <div class="row">
            <div class="col-6">
                {{ estado.valor1 }}
                <input type="number" required @keyup="event => estado.valor1 = event.target.value" placeholder="Digite um valor" class="form-control">
            </div>
            <div class="col-6">
                {{ estado.valor2 }}
                <input type="number" required @keyup="event => estado.valor2 = event.target.value" placeholder="Digite outro valor" class="form-control">
            </div>
            <div class="col-3 mt-5">
                <select id="selectContas" class="form-select" @change="event => estado.filtragemContas(event.target.value)">
                    <option value="adicao" selected>Adição</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
                <label>Resultado da conta: {{ estado.resultado }}</label> 
            </div>
                      
            </div>
        </form>
        
    </div>
    
</template>

<style scoped>

</style>
