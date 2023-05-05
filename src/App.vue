<script setup>

const produtos = [
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.9
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.9
  },
  {
    id: 10,
    nome: 'Meia',
    preco: 9.9
  }
]


</script>

<template>
  <div class="produtos">
    <div v-for="(produto, i) in produtos" :key="i" class="card-produto">
      <h2>{{ produto.nome }}</h2>
      <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
    </div>
  </div>
</template>

<style scoped>
.card-produto {
  width: 300px;
  height: 300px;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.02) 0px 1px 3px 0px, rgba(27, 31, 35, 0.15) 0px 0px 0px 1px;
}

.produtos {
  margin: 200px;
  margin-top: 30px;
  display: grid;
  grid-template-columns: repeat(4, 10fr);
  grid-auto-rows: 400px;
}

</style>
