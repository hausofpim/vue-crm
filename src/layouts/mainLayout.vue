<template>
  <div class="app-main-layout">
    <Navbar @toggle="isOpen = !isOpen" />
    <Sidebar :isOpen="isOpen" />
    <main
      class="app-content"
      :class="{
        full: !isOpen,
      }"
    >
      <div class="app-page">
        <router-view />
      </div>
    </main>

    <div class="fixed-action-btn">
      <router-link to="/record">
        <a class="btn-floating btn-large blue" href="#">
          <i class="large material-icons">add</i>
        </a>
      </router-link>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/app/Navbar.vue";
import Sidebar from "@/components/app/Sidebar.vue";
export default {
  name: "main-layout",
  data: () => ({
    isOpen: true,
  }),
  components: {
    Navbar,
    Sidebar,
  },
};
</script>
