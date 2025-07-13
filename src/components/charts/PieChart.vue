<template>
    <div :class="['pie-chart-grid',gridTemplate]">
        <div :class="[`pie-chart-graph-${props.legendPosition}`]">
            <table :class="['pie-chart-items','charts-css', 'pie', { 'show-heading': showHeading }]">
                <caption v-if="showHeading" class="pie-chart-caption">{{ headingText }}</caption>
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
        <div :class="[`pie-chart-legend-${props.legendPosition}`]">
            <ul :class="['charts-css', 'legend', 'legend-square']"
                :style="{ display: 'grid', fontSize: '1rem', lineHeight: '1.5', justifyContent: 'space-around' }">
                <li v-for="(item, index) in graficoCalculado" :key="index">
                    {{ item?.dataPresentation }}%
                </li>
            </ul>
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
    legendPosition: {
        type: String,
        default: 'bottom',
        validator: value => ['left', 'right', 'bottom'].includes(value)
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
const gridTemplate = computed(() => {
    return {
        'bottom':'grid-template-rows-bottom',
        'left':'grid-template-columns-left',
        'right':'grid-template-columns-right'
    }[props.legendPosition] || 'grid-template-rows-bottom';
})
</script>


<style>
.pie-chart-grid {
    display: grid;
}
.grid-template-rows-bottom {
    grid-template-rows: auto auto;
    grid-template-columns: auto ;
}
.grid-template-columns-left {
    grid-template-rows: auto auto;
    grid-template-columns: 10em auto;
}
.grid-template-columns-right {
    grid-template-columns: auto 10em;
    grid-template-rows: auto auto;
}
.pie-chart-graph-bottom {
    grid-row-start: 1;
}
.pie-chart-legend-bottom {
    padding-top: 1em;
}
.pie-chart-graph-left {
    grid-column-start: 2;
}
.pie-chart-legend-left {
    width:fit-content;
    height:fit-content;
    grid-row-start: 1;
    grid-column-start: 1;
}
.pie-chart-graph-right {
    grid-column-start: 1;
    grid-row-start: 1;
}
.pie-chart-legend-right {
    grid-row-start: 1;
    grid-column-start: 2;
}
</style>