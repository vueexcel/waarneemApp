<template>
  <div>
    <section class="main-content columns">
    <aside class="column is-2 section">
      </aside>
      <div class="container column is-7">
        <nuxt />
      </div>
      <aside class="column is-3 section">
      </aside>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: "Home",
          icon: "home",
          to: { name: "index" },
        },
        {
          title: "Inspire",
          icon: "lightbulb",
          to: { name: "inspire" },
        },
      ],
    };
  },
};
</script>
