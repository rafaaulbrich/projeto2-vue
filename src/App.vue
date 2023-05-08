<script setup>

import { ref } from 'vue'
const produtos = ref([
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/07/26/162727059412a568a162a0c47d7e984178310db6ee_thumbnail_600x.webp'
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/11/01/1635732629edb39539601ef3e3bea0448e7563826c_thumbnail_600x.webp'
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/02/20/16768796992eeaa820f4d37f36542e12b9e93eb4a8_thumbnail_600x.webp'
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9, 
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/05/31/16539936817b8d90d910892f55bcf2d1cff7f6feb2_thumbnail_600x.webp'
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/04/16/168163579245a11de1645f14e1034bc5518a000051_thumbnail_600x.webp'
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/02/24/16772285882e1411abee578b2c7ed014805c00ea41_thumbnail_600x.webp'
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/04/14/16814514652f1e88a8ea24ad3c4f31705ba5b41d46_thumbnail_600x.webp'
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.9,
    quant: 1
  },
  {
    id: 9,
    nome: 'Calcinha',
    preco: 19.9,
    quant: 1
  },
  {
    id: 10,
    nome: 'Sutiã',
    preco: 29.9,
    quant: 1,
  },
  {
    id: 11,
    nome: 'Meia',
    preco: 9.9,
    quant: 1,
  }
])

const carrinho = ref({
  items: [],
  valorTotal: 0,
})

function addPeca(pos) {
    produtos.value[pos].quant++
}

function removerPeca(pos) {
  if (produtos.value[pos].quant > 1) {
    produtos.value[pos].quant--
  }

}

function addCarrinho(i) {
  const produto = produtos.value[i]
  carrinho.value.items.push({...produto, total: produto.preco * produto.quant})
  carrinho.value.valorTotal += produto.preco * produto.quant
}


</script>

<template>
  <div>
    <button @click="carrinhoCompras" class="carrinho">Carrinho</button>
  </div>
  <div class="produtos">
    <div v-for="(produto, i) in produtos" :key="i" class="card-produto">
      <img :src="produto.img">
      <h2>{{ produto.nome }}</h2>
      <p> R$ {{ produto.preco.toFixed(2).replace('.',',') }}</p>
      <p> Quantidade: {{ produto.quant }}</p>
      <div class="botes">
        <button @click="addPeca(i)">+</button>
        <button @click="removerPeca(i)">-</button>
        <button @click="addCarrinho(i)">Adicionar ao carrinho</button>
      </div>
    </div>
  </div>
  <hr>
  <div>
    {{ carrinho }}
  </div>
</template>

<style scoped>
.card-produto {
  width: 300px;
  height: 350px;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-produto img {
  width: 70%;
  
}

.produtos {
  margin: 200px;
  margin-top: 30px;
  display: grid;
  grid-template-columns: repeat(4, 10fr);
  grid-auto-rows: 400px;
}

.carrinho {
  padding: 8px;
  background-color:rgba(88, 84, 84, 0.788);
  border-radius: 5px; 
  border: 0;
}

h2, p {
  margin: 4px;
}

.carrinho:hover{
  background-color:rgba(131, 123, 123, 0.637); 
}

</style>
