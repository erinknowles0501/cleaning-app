<template>
    <div id="app">
        <div v-for="task in tasks" :key="task.uid">{{ task.text}}</div>

        <div v-if="!creating">
            <button type="button" @click="creating = true">Create</button>
        </div>

        <div v-if="creating">
            <TaskCreate @createTask="createTask" />
        </div>
    </div>
</template>

<script>
import { tasks } from "./utilities/data";

import TaskCreate from "./components/TaskCreate";

export default {
    name: "App",
    components: {
        TaskCreate
    },
    data() {
        return {
            tasks: tasks,
            creating: false
        };
    },
    methods: {
        createTask(v) {
            this.creating = false;
            let newTasks = this.tasks;
            newTasks.push(v);
            this.tasks = newTasks;
        }
    }
};
</script>
