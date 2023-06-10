<script setup>
</script>

<template>
    <div class="container">
        <h1 class="mt-5 mb-5 text-center display-1">Calculadora VueJS</h1>
        <div class="row">
            <div class="col-6">
                <input type="text" placeholder="Insira um valor" class="form-control">
            </div>
            <div class="col-6">
                <input type="text" placeholder="Insira outro valor" class="form-control">
            </div>
            <div class="row">
                <div class="col-4 mt-5">
                    <select class="form-select">
                        <option value="adicao">Adição</option>
                        <option value="subtracao">Subtração</option>
                        <option value="multiplicacao">Multiplicação</option>
                        <option value="divisao">Divisão</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
    
</template>

<style scoped>

</style>
