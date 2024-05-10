<template>
    <div class="income-list">
        <income-item v-for="data in state.sortedIncome" :key="data.id" :income="data"/>
    </div>
</template>

<script setup>
    import IncomeItem from './IncomeItem.vue'
    import { defineProps, defineEmits } from 'vue';

    const props = defineProps({
        state: Object
    });
</script>

<style lang="css" scoped>
    .income-list{
        margin-top: 30px;
        padding: 15px;
    }
</style>