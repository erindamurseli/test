<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="todo.titleText" type='text'>
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model="todo.projectText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            todo: {
                titleText: '',
                projectText: '',
            },
            isCreating: false
        }
    },
    methods: {
        openForm() {
            this.isCreating = true;
        },
        closeForm() {
            this.isCreating = false;
        },

        sendForm() {
            
            this.$emit('add-todo', this.todo );
            
            this.newTodoText = '';
            this.isCreating = false;

        }
    }
}
</script>

<style>

</style>