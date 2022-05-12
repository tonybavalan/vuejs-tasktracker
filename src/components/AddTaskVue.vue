<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="">Task</label>
      <input type="text" name="text" v-model="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label for="">Day & time</label>
      <input type="text" name="day" v-model="day" placeholder="Add Day & Time" />
    </div>
    <div class="form-control form-control-check">
      <label for="">Set Remainder</label>
      <input type="checkbox" v-model="remainder" name="remainder" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTaskVue",
  data() {
      return {
      text: '',
      day: '',
      remainder: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if(!this.text){
        alert('Please add a task')
        return
      }

      const newTask = {
        id: Math.floor(Math.random() * 10000),
        text: this.text,
        day: this.day,
        remainder: this.remainder
      }

      console.log(newTask)

      this.$emit('add-task', newTask)
      
      this.task = ''
      this.day = ''
      this.remainder = false

    }
  }
};
</script>


<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>