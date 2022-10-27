<template>
    <li class="flex justify-between bg-white w-full py-1 px-2 rounded-2xl w-full">
        <div class="flex space-x-2 w-full pr-4">
            <input type="checkbox" v-model="editableToDo.done" />
            <div v-if="!editing" @click="toggleEditing()" :class="strikeThroughClass" class="w-full break-all">
                {{ editableToDo.name }}
            </div>
            <input ref="todoRef" type="text" v-else @keydown.enter="$event.target.blur()" @focusout="toggleEditing"
                class="focus:outline-0" v-model="editableToDo.name" />
        </div>
        <button @click="deleteToDo(index)">
            <TrashIcon class="w-5 h-5 hover:text-pink-600 transition duration-150" />
        </button>

    </li>
</template>

<script>
import TrashIcon from './icons/trash.vue'

export default {
    components: {
        TrashIcon
    },
    props: {
        todo: { type: Object, required: true }
    },
    data() {
        return {
            editableToDo: this.todo,
            editing: false
        }
    },
    computed: {
        strikeThroughClass() {
            return this.editableToDo.done ? "line-through" : ""
        }
    },
    methods: {
        deleteToDo(index) {
            this.$emit('delete', index)
        },
        toggleEditing() {
            this.editing = !this.editing;
            if (this.editing) {
                this.$nextTick(() => this.$refs.todoRef.focus())
            }
        }
    }
}
</script>