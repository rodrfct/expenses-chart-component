<script setup>
const res = await fetch('/data.json');
const data = await res.json()

const daysOfWeek = ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat'];
const currentDate = new Date();
const today = daysOfWeek[currentDate.getDay()];

</script>

<template>
    <ul>
        <li v-for="i in data"
         :day="i.day" 
         :class="i.day == today ? 'today' : '' "
         :style="`height: ${150 * i.amount / 100}%;`" ></li>
    </ul>
</template>

<style scoped>

ul {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    align-items: end;
    column-gap: .7rem;

    padding: 0;
    height: 150px;
    margin-bottom: 2.5rem;
}

li {
    position: relative;
    list-style: none;
    background-color: var(--soft-red);
    
    border-radius: 4px;
    height: 0;
    max-height: 100%;
    transition: height 2s ease;
}

li::after {
    content: attr(day);
    position: absolute;
    left: 50%;
    bottom: -1.2rem;

    transform: translate(-50%, 0);
}

/*Apparently support for attr() is very experimental across all browsers
so I used a class binding to get the current day*/
.today {
    background-color: var(--cyan) !important;
}
</style>