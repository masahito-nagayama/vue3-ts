<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

  // const itemName1 = ref<string>('たろう')
  const itemName2 = '麒麟'

  // const price1 = 20000
  const price2 = 50000
  const item1 = reactive({
    name: '権左ぶろう',
    price: 400000
  })

  const url1 = "https://tech-masao.com/"

  const buy = (itemName:string) => {
    alert(itemName + ' を買いますか?')
  }

  const clear = () => {
    item1.name = ''
    item1.price = 0
  }

  const budget = 50000

  const priceLabel = computed(() => {
    if (item1.price > budget) {
      return '高すぎるだろふつうに'
    } else {
      return item1.price + 'yen'
    }
  })
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <input v-model="item1.name" />
    <input v-model="item1.price" />
    <button class="clearButton" @click="clear()">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel }}</label>
      <a v-bind:href="url1">ここで買ったよ！</a>
      <button @click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}yen</label>
      <a v-bind:href="url1">ここで買ったよ！</a>
      <button @click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
  .clearButton {
    margin-bottom: 8px;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .payment {
    display : flex;
    justify-content : space-between;
    align-items: center;
    height: 80px;
    width: 1000px;
    background-color: aliceblue;
    margin-bottom: 10px;
  }

  input {
    margin-bottom: 8px;
  }
  
  label {
    font-size: 20px;
    font-weight: auto;
  }
</style>