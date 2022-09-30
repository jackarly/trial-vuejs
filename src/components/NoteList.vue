<template>
    <h2>All Notes</h2>
    <hr>
    <div v-if="!noteList.length">
        <p>
            Tap the + button to create a note.
        </p>
    </div>

    <div :key="note.id" v-for="note in noteList">
        <div>
            <Note :note="note" 
                @delete-note="$emit('delete-note', note.id)"
                @toggle-update="$emit('toggle-update', note.id)" />
        </div>
    </div>

    <div v-if="noteList.length">
        <small>Double click to edit</small>
    </div>
    

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
    },
    emits: ['delete-note', 'toggle-update'],
}
</script>

<style>
small {
    padding-left: 5px;
    font-style: italic;
}
</style>

