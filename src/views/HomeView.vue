<template>
<div style="width: 20%; height: 20%;">
    <pizza-graph v-bind="{data:graphData}" ></pizza-graph>
</div>
</template>

<script setup>
import { ShowerHead } from 'lucide-vue-next';
import PizzaGraph from '../components/graphs/PizzaGraph.vue';

const graphData = [
    { value:30, dataPresentation: 30 },
    { value:20, dataPresentation: 20 },
    { value:25, dataPresentation: 25 },
    { value:15, dataPresentation: 15 },
    { value:10, dataPresentation: 10 }
];
</script>

<style></style>