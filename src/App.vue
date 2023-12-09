<script setup>
    import { reactive } from 'vue';
    const valores = reactive({
        primeiroValor:' ',
        segundoValor:' ',
        operacao:'todas',
        resultado:' ',
    })

    const getOperacaoSoma = () => {
        valores.resultado = valores.primeiroValor + valores.segundoValor
    }

    const getOperacaoSubtracao = () => {
        valores.resultado = valores.primeiroValor - valores.segundoValor
    } 

    const getOperacaoMultiplicacao = () => {
        valores.resultado = valores.primeiroValor * valores.segundoValor
    }

    const getOperacaoDivisao = () => {
        valores.resultado = valores.primeiroValor / valores.segundoValor
    }

    const getOperacao = () => {
        const operacao = valores.operacao;
        switch (operacao) {
            case 'soma':
                return getOperacaoSoma();
            case 'subtracao':
                return getOperacaoSubtracao();
            case 'multiplicacao':
                return getOperacaoMultiplicacao();
            case 'divisao':
                return getOperacaoDivisao();
            default:
                return valores.resultado;
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
                    <input :value="valores.primeiroValor" @change="evento => valores.primeiroValor = evento.target.value " type="number" placeholder="Digite aqui um valor" class="form-control" id="primeiro-valor"/>
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
                    <input :value="valores.segundoValor" @change="evento => valores.segundoValor = evento.target.value " type="number" placeholder="Digite aqui mais um valor" class="form-control" id="segundo-valor"/>
                </div>
            </div>
        </form>
        <div class="col-md-12">
          <span @change="evento => valores.resultado = evento.target.value"> {{ valores.resultado }} </span>
        </div>
    </div>
</template>

<style scoped>
    input, select, span{
        text-align: center;
        width:400px;
        font-size: 40px;
    }
</style>
