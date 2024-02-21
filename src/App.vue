<script setup>
    import { reactive } from 'vue';

    const valores = reactive({
        primeiroValor: 0,
        segundoValor: 0,
        operacao: 'todas',
    })

    function resultado(){
        const operacao = valores.operacao;
        switch(operacao){
            case 'soma':
                return Number(valores.primeiroValor) + Number(valores.segundoValor);
            case 'subtracao':
                return valores.primeiroValor - valores.segundoValor;
            case 'multiplicacao':
                return valores.primeiroValor * valores.segundoValor;
            case 'divisao':
                return valores.primeiroValor / valores.segundoValor;
            default:
                return 0;
        }
    }

    
</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4 bg-light rounded-3">
            <h1>Calculadora Aritmética</h1>
        </header>
        <form>
            <div class="row">
                <div class="col-md-4">
                    <input @keyup="evento => valores.primeiroValor = evento.target.value" type="number" placeholder="Digite aqui um valor" class="form-control" id="primeiro-valor"/>
                </div>
                <div class="col-md-4">
                    <select @change="evento => valores.operacao = evento.target.value" class="form-control">
                        <option value="todas">Escolha uma Operação</option>
                        <option value="soma">Mais (+)</option>
                        <option value="subtracao">Menos (-)</option>
                        <option value="multiplicacao">Multiplicador por (x)</option>
                        <option value="divisao">Dividido por (/)</option>
                    </select>
                </div>
                <div class="col-md-4">
                    <input @keyup="evento => valores.segundoValor = evento.target.value" type="number" placeholder="Digite aqui mais um valor" class="form-control" id="segundo-valor"/>
                </div>
            </div>
        </form>
        
        <br>
        <hr>
        <h2>primeiro valor: {{ valores.primeiroValor }}</h2>

        <br>
        <h2>segundo valor: {{ valores.segundoValor }}</h2>

        <br>
        <h2>resultado: {{ resultado() }}</h2>
    </div>
</template>

<style scoped>
    input, select, p{
        text-align: center;
        width:400px;
        font-size: 40px;
    }
</style>
