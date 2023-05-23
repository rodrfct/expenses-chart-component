# Frontend Mentor - Expenses chart component solution

This is a solution to the [Expenses chart component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/expenses-chart-component-e7yJBUdjwt). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Useful resources](#useful-resources)


## Overview

### The challenge

Users should be able to:

- [x] View the bar chart and hover over the individual bars to see the correct amounts for each day
- [x] See the current day’s bar highlighted in a different colour to the other bars
- [ ] View the optimal layout for the content depending on their device’s screen size
- [x] See hover states for all interactive elements on the page
- [x] **Bonus**: Use the JSON data file provided to dynamically size the bars on the chart


### Links

- Solution URL: [My Solution]()
- Live Site URL: [My Live Site](https://rodrfct.github.io/expenses-chart-component/)

## My process

### Built with

- CSS Grid
- [Vue](https://vuejs.org/) - JS library



### What I learned

I learned about the `<Suspense>` built-in to display async components

```html
<Suspense>
  <Chart />

  <template #fallback>
    Loading...
  </template>
</Suspense>
```

I came up with this way to make the bars grow

```javascript
// Initial height, must be non-cero but invisible
let height = ref(1)

// After some time, change to 0, so the actual height of the bars is used instead
onMounted(() => {
    setTimeout(() => {
        height.value = 0
    }, 600);
})
```

```html
<template>
    <ul>
        <li v-for="i in data"
         :day="i.day" 
         :amount="`$${i.amount}`"
         :class="i.day == today ? 'today' : '' "
         <!-- This is where the magic happens -->
         :style="height ? `${height}` : `height: ${150 * i.amount / 100}%;`" >
        
        <span class="amount">{{ `$${i.amount}` }}</span>

        </li>
    </ul>
</template>
```

### Useful resources

- [Vue docs](https://vuejs.org/guide/built-ins/suspense.html)
- [W3C Schools](https://www.w3schools.com/css/css_tooltip.asp) - Learned to display the amounts with this article

