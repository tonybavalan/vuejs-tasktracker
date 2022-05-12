<template>
    <div :key="task.id" v-for="task in tasks">
        <TaskVue
            @toggle-remainder="$emit('toggle-remainder', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task" />
    </div>
</template>

<script>
    import TaskVue from './TaskVue'

    export default {
        name: 'TasksVue',
        props: {
            tasks: Array,
        },
        components:{
            TaskVue
        },
        emits: ['delete-task', 'toggle-remainder'],
    }
</script>