<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <nav class="navbar orange lighten-1">
    <div class="nav-wrapper">
      <div class="navbar-left">
        <a href="#" @click.prevent="$emit('toggle')">
          <i class="material-icons black-text">dehaze</i>
        </a>
        <span class="black-text">{{ date }}</span>
      </div>

      <ul class="right hide-on-small-and-down">
        <li>
          <a
            class="dropdown-trigger black-text"
            href="#"
            data-target="dropdown"
            ref="dropdown"
          >
            USER NAME
            <i class="material-icons right">arrow_drop_down</i>
          </a>

          <ul id="dropdown" class="dropdown-content">
            <li>
              <router-link to="/profile">
                <a href="#" class="black-text">
                  <i class="material-icons">account_circle</i>Профиль
                </a>
              </router-link>
            </li>
            <li class="divider" tabindex="-1"></li>
            <li>
              <a href="#" class="black-text" @click.prevent="logout">
                <i class="material-icons">assignment_return</i>Выйти
              </a>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data: () => ({
    date: new Date(),
    interval: null,
    dropdown: null,
  }),
  mounted() {
    this.interval = setInterval(() => {
      this.date =
        new Date().toLocaleTimeString() + " " + new Date().toLocaleDateString();
    }, 1000);
    this.dropdown = window.M.Dropdown.init(this.$refs.dropdown, {
      constrainWidth: true,
    });
  },
  beforeUnmount() {
    /* нужно для того, чтобы не происходили утечки памяти.
    так  интервал и Dropdown будут жить после unmount, 
    то их необходимо удалить*/
    clearInterval(this.interval);
    if (this.dropdown && this.dropdown.destroy) {
      this.dropdown.destroy();
    }
  },
  methods: {
    logout() {
      console.log("logout");
      this.$router.push("/login?message=logout");
    },
  },
};
</script>
