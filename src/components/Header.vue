<template>
    <header>
        <h1>eListahan</h1>
        <button class="btn"
            @click="$emit('toggle-add-note')">
            
            <i class="fa fa-plus"></i>
        </button>
    </header>
</template>

<script>
    export default {
        name: 'Header'
    }
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

h1 {
    font-weight: bold;
}

i {
    color: Green;
    }
</style>