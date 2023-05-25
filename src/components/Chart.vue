<script setup>
import { computed, onMounted, ref } from 'vue';

const res = await fetch('data.json');
const data = await res.json()

const daysOfWeek = ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat'];
const currentDate = new Date();
const today = daysOfWeek[currentDate.getDay()];

const chartHeight = 150
const chartHeightToPixels = computed(() => {
    return `${chartHeight}px`
})

// Initial height, must be non-cero but invisible
const barHeight = ref(1)

// After some time, change to 0, so the actual height of the bars is used instead
onMounted(() => {
    setTimeout(() => {
        barHeight.value = 0
    }, 600);
})

</script>

<template>
    <ul>
        <li v-for="i in data"
         :class="i.day == today ? 'today' : '' "
         :style="barHeight ? '' : `height: ${chartHeight * i.amount / 100}%;`" >
        
        <span class="day">{{ i.day }}</span>
        <span class="amount">{{ `$${i.amount}` }}</span>

        </li>
    </ul>
</template>

<style scoped>

ul {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    align-items: end;
    column-gap: .7rem;

    padding: 0;
    height: v-bind(chartHeightToPixels);
    margin-bottom: 2.5rem;
}

li {
    position: relative;
    list-style: none;
    background-color: var(--soft-red);
    
    border-radius: 4px;
    height: 0;
    max-height: 100%;
    transition: height 2s ease, filter .5s ease;
}

.day {
    position: absolute;
    left: 50%;
    bottom: -1.2rem;

    transform: translate(-50%, 0);
}

li:hover {
    cursor: pointer;
    filter: brightness(130%);
}

.amount {
    visibility: hidden;
    position: absolute;
    top: -35px;
    left: 50%;
    transform: translate(-50%, 0);

    text-align: center;
    color: var(--very-pale-orange);

    padding: .4em;
    background-color: var(--dark-brown);
    border-radius: 3px;
}

li:hover .amount{
    visibility: visible;
}

/*Apparently support for attr() is very experimental across all browsers
so I used a class binding to get the current day*/
.today {
    background-color: var(--cyan) !important;
}
</style>