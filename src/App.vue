<template>
  <main>
    <user-list :users="activeUsers" @list-projects="selectUser"></user-list>
    <projects-list :user="selectedUser"></projects-list>
  </main>
</template>

<script>
import {ref} from 'vue';

import USER_DATA from './dummy-data.js';

import UserList from './components/users/UserList.vue';
import ProjectsList from './components/projects/ProjectsList.vue';

export default {
  components: {
    UserList,
    ProjectsList,
  },
  setup() {
    const selectedUser =ref(null);
    const activeUsers = USER_DATA;

    function selectUser(uid){
      selectedUser.value = activeUsers.find((usr) => usr.id === uid)
    }

    return {
      selectedUser,
      activeUsers,
      selectUser
    }
  },
  // data() {
  //   return {
  //     selectedUser: null,
  //     activeUsers: USER_DATA,
  //   };
  // },
  // methods: {
  //   selectUser(uid) {
  //     this.selectedUser = this.activeUsers.find((usr) => usr.id === uid);
  //   },
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: sans-serif;
}
body {
  margin: 0;
}

main {
  display: flex;
  justify-content: space-around;
}

button {
  font: inherit;
  border: 1px solid #EA7317;
  background-color: transparent;
  color: #EA7317;
  padding: 0.5rem 1.5rem;
  cursor: pointer;
  margin: 0.5rem 0.5rem 0.5rem 0;
}
button:hover,
button:active {
  background-color: #FEC601;
}

button.selected {
  background-color: #FEC601;
  color: EA7317;
}
</style>