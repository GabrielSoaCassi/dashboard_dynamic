<template>
    <div>
        <ul :class="['charts-css', 'legend', 'legend-square']"
            :style="{ fontSize: '1rem', lineHeight: '1.5'}">
            <li v-for="(item, index) in data" :key="index">
                {{ item?.dataPresentation }}%
            </li>
        </ul>
    </div>
</template>

<script setup>

const props = defineProps({
    data: {
        type: Array,
        required: true
    }
});
</script>


<style></style>