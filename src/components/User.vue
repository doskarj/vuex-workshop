<template>
  <div class="user">

    <h2>{{ user.name }}</h2>
    <a :href="'mailto:' + user.mail">{{ user.email }}</a>
    <br>
    <span>{{ user.phone }}</span>
    <br>
    <button v-if="isRemovable" @click="removeUser">Remove</button>

  </div>
</template>

<script>
export default {
  name: 'User',
  props: ['user', 'isRemovable'],
  methods: {
    removeUser () {
      this.$emit('removeUser', this.user.id);
    }
  }
}
</script>

<style scoped>
.user {
  position: relative;
  width: 300px;
  height: 75px;
  padding: 15px;
  margin: 10px 0px;
  background-color: #dce775;
  border-radius: 10px;
}
.user h2 {
  margin-top: 0px;
  margin-bottom: 5px;
}
.user a {
  display: inline-block;
  margin-bottom: 5px;
}
button {
  position: absolute;
  right: 10px;
  bottom: 10px;
}
</style>
