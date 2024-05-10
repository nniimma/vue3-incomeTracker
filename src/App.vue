<script setup>
  import Header from "./components/Header.vue";
  import {reactive, computed} from 'vue'
  import Form from './components/Form.vue'
  import IncomeList from './components/IncomeList.vue'

  const state =  reactive({
    income: [],
    totalIncome: computed(() => {
      let temp = 0

      if(state.income.length > 0){
        for(let i = 0; i < state.income.length; i++){
          temp += state.income[i].value
        }
      }

      return temp
    }),
    sortedIncome: computed(() => {
        let temp = [];
        
        temp = state.income.sort(function (a, b) {
          return b.date - a.date;
        });

        return temp;
      })
  })

  function AddIncome(data){
    let d = data.date.split('-')
    let newD = new Date(d[0], d[1], d[2]);

    state.income = [...state.income, {
      id: Date.now(),
      desc: data.desc,
      value: data.value,
      date:newD.getTime()
    }]
  }
</script>

<template>
  <main>
    <Header :totalIncome="state.totalIncome"/>
    <Form @add-income="AddIncome"/>
    <income-list :state="state"/>
  </main>
</template>

<style scoped>
  * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

main {
  background: #eeeeee;
  height: 100vh;
}
</style>
