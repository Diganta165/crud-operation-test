<template>
  <div>
      <tr>
          <td>{{user.id}}</td>
          <td>{{user.name}}</td>
          <td>{{user.email}}</td>
          <td>
              <button >Edit</button>
              <button @click="onDelete">Delete</button>
          </td>
      </tr>
  </div>
</template>

<script>
export default {
props:{
    user:Object
},
methods:{
    onDelete(){
        // console.log('Deleted', this.user.id)
        this.$emit("onDelete", this.user.id)
    }
}
}
</script>

<style>

</style>