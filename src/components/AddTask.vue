<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Note</label>
            <input type="text" v-model="text" name="text" placeholder="Add note">
        </div>
        <div class="form-control">
            <label>DateTime</label>
            <input type="text" v-model="day" name="datetime" placeholder="Add date and time">
        </div>
        <div class="form-control form-control-check">
            <label>to Mark</label>
            <input type="checkbox" v-model="reminder" value="reminder">
        </div>
        <div class="form-control">
            <input type="submit" value="Save" class="btn btn-block">
        </div>
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e){
            e.preventDefault()
            if(!this.text){
                alert('Please, write your note')
                return
            }
            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)
            
            console.log(newTask);
            this.text = ''
            this.day = ''
            this.reminder = false
        }
    }
}
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