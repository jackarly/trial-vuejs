<template>
    <div @dblclick="$emit('toggle-update', note.id)" class="note">
        <h3>{{ note.title }}
            <i class="fa fa-times"
                @click="onDelete(note.id)" >
            </i>
        </h3>
        <p>{{ note.date }}</p>
    </div>
</template>

<script>
export default {
    name: 'Note',
    props: {
        note: Object
    },
    methods: {
        onDelete(id){
            // console.log(id)
            this.$emit('delete-note', id)
        }
    }
}
</script>

<style scope>
.fa-times {
    color: red;
}

.note {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.note h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
i {
    color: Green;
}
</style>