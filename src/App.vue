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
    quant: 1,
    img: 'https://img.ltwebstatic.com/gspCenter/goodsImage/2022/10/10/5445485991_1005024/98FE5FA6BD05192CC2E0A8482B0BBD7F_thumbnail_600x.jpg'
  },
  {
    id: 9,
    nome: 'Calcinha',
    preco: 19.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/08/11/1628647984061320a79ab1f4054b1e93e30e89d368_thumbnail_600x.webp'
  },
  {
    id: 10,
    nome: 'Sutiã',
    preco: 29.9,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2020/07/24/1595566126b0e86e8be48ae4f01a61ae74934eb027_thumbnail_600x.webp'
  },
  {
    id: 11,
    nome: 'Brinco',
    preco: 15.99,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/11/29/1638174388f2c5d01a3a08d65da9320b143bf32b1d_thumbnail_600x.webp'
  },
  {
    id: 12,
    nome: 'Colar',
    preco: 10.99,
    quant: 1,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/10/27/166685854459b02edcff5682b46bbf1fdaec2c41d3_thumbnail_600x.webp'
  }
])

const carrinho = ref({
  items: [],
  valorTotal: 0,
})

function carrinhoCompras() {
  
}

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
    <button @click="carrinhoCompras" class="carrinho">
      Carrinho
      <img src="https://cdn.icon-icons.com/icons2/1760/PNG/512/4105931-add-to-cart-buy-cart-sell-shop-shopping-cart_113919.png" class="img-carrinho">
    </button>
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
  <div>
    {{ carrinho }}
  </div>
</template>

<style scoped>
.card-produto {
  width: 300px;
  height: 450px;
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-produto img {
  margin-top: 30px;
  width: 70%;
}
.produtos {
  margin: 200px;
  margin-top: 30px;
  margin-left: 10%;
  display: grid;
  grid-template-columns: repeat(4, 27%);
  grid-auto-rows: 40%;
}
.carrinho {
  width: 8%;
  margin-left: 10%;
  padding: 10px;
  background-color: rgb(190, 185, 185);
  border-radius: 5px;
  border: 1px solid gray;
  font-family: 'Times New Roman', Times, serif;
  font-size: 20px;
  transition: all 0.2s;
}
.carrinho:hover{
  transition: 0.2s;
  transform: scale(1.1);
  background-color:rgb(230, 227, 227); 
}


.img-carrinho {
  width: 20px;
  height: 20px;
}

p {
  color: rgb(78, 78, 78);
}

h2, p {
  margin: 4px;
}

button {
  background-color:rgb(190, 185, 185);
  border-radius: 4px;
  border: 1px solid gray;
  font-family: 'Times New Roman', Times, serif;
  margin: 2px;
}

button:hover {
  background-color: rgb(230, 227, 227);
}

</style>
