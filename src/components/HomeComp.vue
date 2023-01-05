<template>
    <v-container fluid>
        <v-row class="justify-center">
                <h1 class="text-h2 mt-10">TO DO</h1>
        </v-row>
        <v-row class="justify-center mt-10" width="1000">
            <v-form @submit.prevent="addToDo">
                <v-text-field label="Add To Do" size="50" v-model="newToDo">
                </v-text-field>
            </v-form>
        </v-row>

        <v-row class="justify-center mt-10" max-width="100%">
            <div v-for="(todo, index) in toDoList" :key=todo.id>
                 <v-card class="mx-auto pl-3 pt-3 mt-5" elevation="3" width="1000">
                    <v-card-title class="text-h5 ">{{todo.name}}</v-card-title>
                    <v-card-actions>
                        <v-btn text color="green" @click="removeToDo(index)">Done</v-btn>
                    </v-card-actions>
                </v-card>
            </div>
        </v-row>
    </v-container>      
</template>
<script>
    import {ref} from 'vue';
    export default{
        setup(){
            const toDoList = ref([]);
            const newToDo = ref('');
            
            function addToDo(){
                toDoList.value.push({
                    name: newToDo.value,
                    id: Date.now()
                })
                newToDo.value = '';
            }
            function removeToDo(ind){
                toDoList.value.splice(ind,1);
            }

            return {
                toDoList,
                addToDo,
                newToDo,
                removeToDo
            }
        }
    }
</script>
<style scoped>

</style>
