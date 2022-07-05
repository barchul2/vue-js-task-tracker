
<template>

    <section class="button">
        <button @click="onClick()" :style="{ background: color }">
            {{ value }}
        </button>
    </section>
</template>

<script>
export default {
    name: 'Button',
    props: {
        color: String,
        value: String
    },
    methods: {
        onClick() {
            console.log('This Button Got Clicked')
        }
    }
}
</script>

