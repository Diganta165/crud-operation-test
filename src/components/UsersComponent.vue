<template>
  <div>
      <table>
          <tr>
              <th>No</th>
              <th>Name</th>
              <th>Email</th>
              <th>Action</th>

          </tr>
          <tr>
              <user-component v-for="user in users" :key="user.id" :user = "user"/>
          </tr>
      </table>
  </div>
</template>

<script>
import UserComponent from './UserComponent.vue'
export default {
components:{
UserComponent
    
},
props: {
    users :{
        type:Array
    }
}
}
</script>

<style>

</style>