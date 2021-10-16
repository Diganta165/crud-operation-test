<template>
  <div>
    <form>
      <input type="text" name="name" :value="form.name" placeholder="Name" @change="handleChange" />
      <input type="text" name="email" :value="form.email" placeholder="Email" @change="handleChange"/>
      <!-- <input type="text" name="" placeholder="Name" /> -->
      <button @click="onFormSubmit">Save</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    form: {
      type: Object,
    },
  },
  methods:{
      handleChange(event){
          const {name, value} = event.target ;
          let form = this.form;
          form[name] = value;
          this.form = form;

      },
      onFormSubmit(e){
          e.preventDefault();

          if(this.formValidation()){
              console.log('ready to submit')
              this.$emit("onFormSubmit", this.form)
          }
      },
      formValidation(){
          if(document.getElementsByName('name')[0].value === ""){
              alert("Enter Name");
              return false;
          }
          if(document.getElementsByName('email')[0].value === ""){
              alert("Enter Email");
              return false
          }
      }
  }
};
</script>

<style>
</style>