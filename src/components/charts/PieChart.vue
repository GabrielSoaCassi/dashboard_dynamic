<template>
    <div>
        <div >
            <table :class="[
                'charts-css',
                'pie',
                { 'show-heading': showHeading }]">
                <caption v-if="showHeading">{{ headingText }}</caption>
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
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    showHeading: {
        type: Boolean,
        default: false
    },
    headingText: {
        type: String,
        default: 'Pie Chart'
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
</style>