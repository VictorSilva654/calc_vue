<script setup>
import { reactive, watch } from 'vue';

const estado = reactive({
    valor1: 0,
    valor2: 0,
    resultado: 0,
    operacao: 'adicao',
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
                if (estado.valor1 == 0 || estado.valor2 == 0) {
                    estado.resultado = "Não existe divisão por Zero, insira outro valor";
                }
                return estado.resultado  
        }
    }
})

watch(() => [estado.valor1, estado.valor2, estado.operacao], () => {
    estado.filtragemContas(estado.operacao);
})


</script>

<template>
    <div class="container">
        <h1 class="mt-5 mb-5 text-center display-1">Calculadora VueJS</h1>
        <form>
            <div class="row">
                <div class="col-6">
                    <input type="number" required @keyup="event => estado.valor1 = event.target.value" placeholder="Digite um valor" class="form-control">
                </div>
                <div class="col-6">
                    <input type="number" required @keyup="event => estado.valor2 = event.target.value" placeholder="Digite outro valor" class="form-control">
                </div>    
            </div>
            <div class="row mt-5 d-flex">
                <div class="col-3 col-sm-6">
                    <select id="selectContas" class="form-select d-flex" v-model="estado.operacao">
                        <option value="adicao" selected>Adição</option>
                        <option value="subtracao">Subtração</option>
                        <option value="multiplicacao">Multiplicação</option>
                        <option value="divisao">Divisão</option>
                    </select>
                </div>
                <label class="mt-5">Resultado da conta: {{ estado.resultado }}</label> 
            </div>
        </form>
    </div>
    
</template>

<style scoped>
    
</style>
