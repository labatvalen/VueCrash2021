<template>
    <!-- Si reminder est vrai, on ajoute la classe reminder, sinon rien
        et on veut également la classe task
         Event en double cliquant sur la div
         emit renvoie au cran en dessus, ici à Tasks.vue-->
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}
            <i @click="onDelete(task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{task.day}}</p>
    </div>
</template>

<script>
    export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-task', id)
        }
    }
}
</script>

<style scope>
    .fas {
        color: red;
    }
    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .task.reminder {
        border-left: 5px solid green;
    }
    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>