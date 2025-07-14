<template>
    <div>
        <table :class="[
            'charts-css',
            'bar',
            `data-${position}`,
            `data-${spacing}`,
            orientation,
            {
                'show-labels': showLabels,
                'hide-data': hideData,
                'show-heading': showHeading,
                'show-data-on-hover': showDataOnHover,
                'show-primary-axis': showPrimaryAxis,
                'show-data-axes': showDataAxes

            }
        ]">
            <caption v-if="showHeading" class="bar-chart-caption"><em>{{ headingText }}</em></caption>
            <tbody>
                <tr v-for="(item, index) in data" :key="index">
                    <th scope="row" :class="[{ 'hide-label': item.hideLabel }]"> {{ item?.dataPresentation }}%</th>
                    <td :style="{ '--size': `calc(${item.value}/${total})` }">
                        <span :class="['data', { 'outside': item?.outside }]">{{ item?.dataPresentation }}%</span>
                    </td>

                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    showHeading: {
        type: Boolean,
        default: false
    },
    showPrimaryAxis: {
        type: Boolean,
        default: false
    },
    showDataAxes: {
        type: Boolean,
        default: false
    },
    orientation:{
        type:String,
        default:'',
        valdiator: value => ['reverse','reverse-labels','reverse-data']
    },
    position: {
        type: String,
        default: 'start',
        validator: value => ['start', 'end', 'outside', 'center'].includes(value)
    },
    spacing: {
        type: Number,
        default: 0
    },
    hideData: {
        type: Boolean,
        default: false
    },
    showLabels: {
        type: Boolean,
        default: false
    },
    showDataOnHover: {
        type: Boolean,
        default: false
    },
    headingText: {
        type: String,
        default: 'Bar Chart'
    },
    data: {
        type: Array,
        required: true
    }
});
const total = computed(() => props.data.reduce((acc, item) => acc + item.value, 0))

</script>


<style></style>