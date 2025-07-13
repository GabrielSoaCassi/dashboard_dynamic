<template>
    <div class="pie-graph">
        <table :class="['charts-css', 'pie', { 'show-heading': showHeading }]">
            <caption v-if="showHeading">Pizza Graph</caption>
            <tbody>
                <tr v-for="(item, index) in graficoCalculado" :key="index">
                    <td :style="{
                        '--start': `${item.start}`,
                        '--end': `${item.end}`
                    }">
                        <span class="data">{{ item?.dataPresentation }}%</span>
                    </td>
                </tr>
            </tbody>
        </table>
        <ul class="charts-css legend legend-square">
            <li v-for="(item, index) in graficoCalculado" :key="index">
                {{ item?.dataPresentation }}%
            </li>
        </ul>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    showHeading: {
        type: Boolean,
        default: false
    },
    data: {
        type: Array,
        required: true
    }
});
const total = computed(() => props.data.reduce((acc, item) => acc + item.value, 0))
const graficoCalculado = computed(() => {
    let acumulado = 0;
    return props.data.map(item => {
        const start = acumulado / total.value;
        acumulado += item.value;
        const end = acumulado / total.value;

        return {
            ...item,
            start,
            end
        };
    });
});
</script>


<style>
.pie-graph {
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr;
}
</style>