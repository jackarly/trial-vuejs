<template>
    <header>
        <h1>eListahan</h1>
        <button class="btn"
            @click="onClick()">
            
            <i class="fa fa-plus"></i>
        </button>
        
    </header>
</template>

<script>
export default {
    name: 'Header',
    methods: {
        onClick() {
            console.log('click')
        },
    },
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>