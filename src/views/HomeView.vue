<template>
<div style="width: 40%; height: 20%;">
    <bar-chart v-bind="{data:graphData}" ></bar-chart>
    <pie-chart v-bind="{data:graphData}" ></pie-chart>
</div>
</template>

<script setup>
import PieChart from '../components/charts/PieChart.vue';
import BarChart from '../components/charts/BarChart.vue';
const graphData = [
    { value:30, dataPresentation: 30 },
    { value:20, dataPresentation: 20 },
    { value:25, dataPresentation: 25 },
    { value:15, dataPresentation: 15 },
    { value:10, dataPresentation: 10 }
];
</script>

<style></style>