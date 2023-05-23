<script setup>
import Chart from './Chart.vue';

</script>

<template>
    <div class="card">
        <p id="title" class="bold">Spending - Last 7 days</p>

        <Suspense>
            <Chart />

            <template #fallback>
                Loading...
            </template>
        </Suspense>

        <hr>

        <div id="months-info">
            <div>
                <p>Total this month</p>
                <p class="bold" id="total" >$478.33</p>
            </div>

            <div id="last-month">
                <p class="bold">+2.4%</p>
                <p>from last month</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    border-radius: 15px;
    background-color: var(--very-pale-orange);
    padding: .5rem 1.5rem;

    color: var(--medium-brown);
    font-size: .8rem;
}

#title{
    font-size: 1.3rem;
}

#total {
    font-size: 2rem;
}

.bold {
    font-weight: 700;
    color: var(--dark-brown)
}

hr {
    border: none;
    border-top: 1px solid var(--medium-brown);
    margin: 1.7rem 0;
}

#months-info {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

#months-info p {
    margin: 0.2rem 0;
}

#last-month .bold {
    text-align: right;
}
</style>