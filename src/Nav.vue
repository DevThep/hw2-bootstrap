<template lang="html">
     <b-navbar toggleable type="inverse" variant="inverse">
            <b-nav-toggle target="nav_collapse"/>
            <a class="navbar-brand" style="color:#E0FFFF" to="/">
                <span>Bootstrap</span>
            </a>
            <b-collapse is-nav class="redirect" id="nav_collapse">
                <b-nav is-nav-bar>
                    <router-link :to="{ name: 'Posts.index' }">
                    <b-nav-item class="hov">
                        <i class="material-icons">message</i>
                        <span>Posts</span>
                    </b-nav-item>
                    </router-link>
                    <router-link :to="{ name: 'Posts.new' }">
                    <b-nav-item class="hov">
                        <i class="material-icons">note_add</i>
                        <span>Add New Post</span>
                    </b-nav-item>
                    </router-link>
                </b-nav>
                <b-nav is-nav-bar class="ml-auto">
                    <b-nav-item class="hov">
                        <i class="material-icons">eject</i>
                        <span style="font-weight: bold;" @click="logout">Log Out</span>
                    </b-nav-item>
                </b-nav>
            </b-collapse>
        </b-navbar>
</template>

<script>
import UserApi from '@/api/users.js'
export default {
  methods: {
    toggleLeftSidenav () {
      this.$refs.leftSidenav.toggle()
    },
    logout () {
      UserApi.logout()
    }
  }
}
</script>

<style lang="css">
    .redirect span {
        color: #FF4500;
    }

    .redirect .hov:hover {
        background-color: #708090;
    }
</style>
