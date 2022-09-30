<template>
    <div :key="note.id" v-for="note in noteList">
        <div>
            <Note :note="note" />
        </div>
    </div>
    <small>Double click to edit</small>
</template>

<script>
import Note from './Note.vue'

export default {
    name: 'NoteList',
    props: {
        noteList: Array,
    },
    components: {
        Note,
    }
}
</script>

