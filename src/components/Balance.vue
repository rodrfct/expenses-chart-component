<template>
    <div class="card">
        <div class="text">
            <p>My balance</p>
            <p class="balance">$921.48</p>
        </div>

        <img src="../assets/img/logo.svg" alt="">
    </div>
</template>

<style scoped>
.card {
    background-color: var(--soft-red);
    border-radius: 15px;
    padding: .7rem 1.5rem;
    color: var(--very-pale-orange);

    display: flex;
    justify-content: space-between;
}

p {
    font-size: .7rem;
    margin: .4rem 0;
}

.balance {
    font-size: 1.2rem;
    font-weight: 700;
}

img {
    width: 3rem;
}
</style>