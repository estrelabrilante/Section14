<template>
  <!-- transition group: animating individual list item as well as multiple list item -->
  <transition-group tag="ul" name="user-list">
    <li v-for="user in users" :key="user" @click="removeUser(user)">
      {{ user }}
    </li>
  </transition-group>

  <div>
    <input type="text" />
    <button @click="addUser" ref="userNameInput">Add Users</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      users: ['Suhail', 'Sunil', 'Shynu', 'Jini', 'Megha']
    };
  },
  methods: {
    addUser() {
      const enteredUserName = this.$refs.userNameInput.value;
      this.users.unshift(enteredUserName);
    },
    removeUser(user) {
      this.users = this.users.filter(usr => usr !== user);
    }
  }
};
</script>
<style scoped>
ul {
  list-style: none;
  margin: 1rem 0;
  padding: 10;
}
li {
  border: 10px solid #ccc;
  padding: 1rem;
  text-align: center;
}
.user-list-enter-to {
  opacity: 0;
  transform: translateX(-30px);
}

.user-list-enter-active {
  transition: all 0.3s ease-out;
}
.user-list-enter-from {
  opacity: 1;
  transform: translateX(0);
}
.user-list-leave-to {
  opacity: 1;
  transform: translateX(0);
}

.user-list-leave-active {
  transition: all 1s ease-in;
}
.user-list-leave-from {
  opacity: 0;
  transform: translateX(30px);
}
</style>
