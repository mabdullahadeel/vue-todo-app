<template>
    <div id="overlay">
        <div class="container">
            <div class="input">
                <input v-model="inputValue" type="text" placeholder="Type Text...">
            </div>
            <div class="button">
                <button @click="handleSubmit">Ok</button>
            </div>
            <div class="button">
                <button @click="closeModal">Cancel</button>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "TaskModal",
    props: {
        closeModal: Function,
        tasks: Array,
        mode: String,
        currentID: Number | null
    },
    data(){
        return {
            inputValue: ""
        }
    },
    methods: {
        handleSubmit(){
            if (this.mode === "add" && this.inputValue){
                this.tasks.unshift({
                    id: this.tasks.length + 1,
                    task: this.inputValue,
                    status : "PENDING"
                })
                this.inputValue = ""
                this.closeModal()
            } else if (this.mode === "update"){
                console.log("updatemode")
            }
        }
    },
    mounted(){
        if (this.currentID){
            const currentTask = this.tasks.filter(task => task.id === this.currentID)
            this.inputValue = currentTask[0].task
        }
    }
}

</script>

<style scoped>
    #overlay {
        position: fixed;
        width: 100%; 
        height: 100%; 
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: rgba(0,0,0,0.5); 
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .container{
        height: 30vh;
        width: 40vw;
        background: rgb(65, 143, 78);
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        z-index: 2;
    }

    .input{
        width: 100%;
        padding: 10px 30px;
    }

    .input > input {
        padding: 10px;
        height: 50px;
        width: 100%;
        font-family: inherit;
        border: none;
        outline: none;
        box-shadow: 5px 10px 30px #3a7230
    }

    .button > button{
        height: 50px;
        width: 400px;
        border: none;
        outline: none;
        font-family: inherit;
        font-size: 30px;
        background: rgb(91, 204, 91);
        color: rgb(2, 58, 9);
        margin-top: 20px;
        cursor: pointer;
    }

    .button > button:active {
    transform: scale(0.98);
    }
</style>