<template>
    <div class="income-item">
        <div class="removeItem">X</div>
        <div class="desc">{{ income.desc }}</div>
        <div class="price">${{ income.value }}</div>
        <div class="date">{{ formattedDate }}</div>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(["add-income"])

const props = defineProps({
    income: Object
});

let date = new Date(props.income.date); // Accessing income from props
let day = date.getDate();
let month = date.getMonth() + 1; // Adding 1 because getMonth() returns zero-based month (0-11)
let year = date.getFullYear();
let formattedDate = `${day}/${month}/${year}`;

</script>

<style lang="css" scoped>
      .income-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #FFF;
    border-radius: 8px;
    max-width: 600px;
    margin: 0 auto 30px;
  }

  .removeItem {
    color: #EF2D2D;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
    cursor: pointer;
  }

  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }

  .price {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }

  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
</style>