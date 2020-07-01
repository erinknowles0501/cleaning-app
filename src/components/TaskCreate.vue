<template>
    <div>
        <h3>Create a new task</h3>
        <input type="text" placeholder="Task title" v-model="newTask.text" />
        <br />
        <input type="number" placeholder="Recurs after how many days?" v-model="newTask.period" />
        <br />
        <select v-model="newTask.points">
            <option :value="1">1</option>
            <option :value="2">2</option>
            <option :value="3">3</option>
            <option :value="5">5</option>
            <option :value="8">8</option>
            <option :value="13">13</option>
        </select>
        <br />
        <button type="button" @click="createTask">Create</button>
    </div>
</template>


<script>
export default {
    name: "TaskCreate",
    data() {
        return {
            newTask: {
                uid: null,
                text: "",
                period: null,
                points: null
            }
        };
    },
    methods: {
        createTask() {
            this.$emit("createTask", this.newTask);
        }
    }
};
</script>