<template>
    <button class="sm-btn" :class="selectColorClass()">{{text}}</button>
</template>


<script>
    export default {
        name: "TaskButton",
        props: {
            text: String,
            role: String
        },
        methods: {
            selectColorClass(){
                switch (this.role) {
                    case "delete":
                        return "red";
                    case "update":
                        return "blue"
                    case "complete":
                        return "complete"
                    case "pending":
                        return "pending"
                    default:
                        return "green";
                }
            }
        }
    }
</script>

<style scoped>
    .sm-btn{
        height: 30px;
        width: auto;
        color: white;
        margin: 0px 10px;
        padding: 0px 15px;
        cursor: pointer;
        border: none;
        margin: 5px;
        border-radius: 5px;
        text-decoration: none;
        font-size: 15px;
        font-family: inherit;
    }

    .blue {
        background: rgb(84, 84, 211);
    }

    .red{
        background: rgb(240, 136, 136);
    }
    .complete{
        background: rgb(91, 71, 138);
    }
    .pending{
        background: rgb(155, 107, 45);
    }
    .green{
        background: rgb(184, 246, 241);
    }

</style>