<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <ul
    class="sidenav app-sidenav"
    :class="{
      open: isOpen,
    }"
  >
    <router-link
      active-class="active"
      :to="link.url"
      v-for="link in links"
      :key="link.url"
    >
      <li>
        <a href="#" class="waves-effect waves-orange pointer">{{
          link.title
        }}</a>
      </li>
    </router-link>
  </ul>
</template>

<script>
export default {
  props: ["isOpen"],
  data: () => ({
    links: [
      {
        title: "Счет",
        url: "/",
      },
      {
        title: "История",
        url: "/history",
      },
      {
        title: "Планирование",
        url: "/planning",
      },
      {
        title: "Новая запись",
        url: "/record",
      },
      {
        title: "Категории",
        url: "/categories",
      },
    ],
  }),
};
</script>
