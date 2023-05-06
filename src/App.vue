<script setup>

const produtos = [
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quant: 1
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quant: 1
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quant: 1
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9, 
    quant: 1
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9,
    quant: 1
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9,
    quant: 1
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9,
    quant: 1
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.9,
    quant: 1
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.9,
    quant: 1
  },
  {
    id: 10,
    nome: 'Meia',
    preco: 9.9,
    quant: 1
  }
]

function addPeca() {
    quant.value++
}

function removerPeca() {
  if(quant > 0) {
    quant.value--
  }
}


</script>

<template>
  <div class="carrinho">
    <button @click="carrinhoCompras">Carrinho</button>
  </div>
  <div class="produtos">
    <div v-for="(produto, i) in produtos" :key="i" class="card-produto">
      <h2>{{ produto.nome }}</h2>
      <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
      <p> Quantidade: {{ produto.quant }}</p>
      <button @click="addPeca">+</button>
      <button @click="removerPeca">-</button>
      <button @click="addCarrinho">Adicionar ao carrinho</button>
    </div>
  </div>
</template>

<style scoped>
.card-produto {
  width: 300px;
  height: 300px;
  border-radius: 10px;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.produtos {
  margin: 200px;
  margin-top: 30px;
  display: grid;
  grid-template-columns: repeat(4, 10fr);
  grid-auto-rows: 400px;
}

h2, p {
  margin-left: 20px;
}

</style>
