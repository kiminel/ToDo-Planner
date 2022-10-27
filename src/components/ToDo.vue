<template>
    <li class="flex justify-between bg-white w-full py-1 px-2 rounded-2xl w-full">
        <div class="flex space-x-2">
            <input type="checkbox" v-model="editableToDo.done" />
            <input type="text" :class="strikeThroughClass" v-model="editableToDo.name" />
        </div>
        <button @click="deleteToDo(index)">
            <TrashIcon class="w-5 h-5 hover:text-pink-600 transition duration-150"/>
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
            editableToDo: this.todo
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
        }
    }
}
</script>