<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
    
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object
        },
    }

    
</script>

<style scoped>
    .fas {
        color: #ff0000;
    }

    .task {
        background: #ebe5e5;
        margin: 5px 0;
        padding: 10px 20px;
        cursor: pointer;
    }

    .task.reminder {
        border-left: 3px solid #36da36;
    }

    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }


</style>