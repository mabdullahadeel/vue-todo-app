<template>
        <div class="task-container">
            <div class="task-heading"><h1>Manage Tasks</h1></div>
            <div v-if="tasks.length > 0" class="task-body">
                <div class="single-task" v-for="task in tasks" :key="task.id">
                    <div class="task-name">{{ task.task }}</div>
                    <div class="task-status">{{ task.status === "PENDING" ? "PENDING 🔃" : "DONE ✅" }}</div>
                    <div class="task-btn">
                        <TaskButton
                            @click="updateTask(task.id)"
                            text="Update"
                            role="update"
                        />
                        <TaskButton
                            @click="deleteTask(task)"
                            text="Delete"
                            role="delete"
                        />
                        <TaskButton
                            @click="handleMarkCompleteIncomplete(task.id)"
							:text= "task.status === 'PENDING' ? 'Mark Complete  ' : 'Mark Incomplete'"
                            :role= "task.status === 'PENDING' ? 'complete': 'pending'"
                        />
                    </div>
                </div>
            </div>
            <div class="footer">
                <Button buttonText="Add Task +" @click="OpenAddTaskModal()" color="#2ea5c9" />
                <Button buttonText="Remove Task -" color="#e6608d" @click="removeAllTasks"/>
            </div>
        </div>
</template>

<script>
import Button from './Button'
import TaskButton from './TaskButton'
export default {
    name: 'TaskContainer',
    components: {
        Button,
        TaskButton,
    },
    props: {
        tasks: Array,
        OpenAddTaskModal: Function,
        updateTask: Function,
    },
    data() {
        return {
            check: false,
        }
    },
    created() {
        console.log(this.tasks)
    },
    methods: {
        deleteTask(task) {
            let ind = this.tasks.indexOf(task)
            this.tasks.splice(ind, 1)
        },
        handleMarkCompleteIncomplete(currentID){
            const n = this.tasks.filter(task => task.id === currentID)
            if (n[0].status === "PENDING") n[0].status = "DONE"
            else if (n[0].status === "DONE") n[0].status = "PENDING"
        },
        removeAllTasks(){
            for (let i = this.tasks.length; i > 0; i--) {
                this.tasks.pop();
            }
        }
    },
}
</script>

<style scoped>

.task-container {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 1100px;
    border: 1px solid #eee;
    border-radius: 10px;
}

.task-heading,
.footer {
    flex: 0.15;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.task-heading{
    position: sticky;
    top: 0;
    background: whitesmoke;
}

.footer{
    position: sticky;
    bottom: 0;
    background: whitesmoke;
}

.task-body {
    flex: 0.7;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 100%;
}

.single-task {
    width: 100%;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    border: 1px solid #eee;
}
.single-task:hover{
    background: #eee;
    cursor: pointer;
}

.task-name {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    flex: 0.5;
    padding-left: 30px;
    margin-right: 30px;
    overflow: hidden;
}

.task-status{
    flex: 0.15;
}

.task-btn{
    flex: 0.35;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
