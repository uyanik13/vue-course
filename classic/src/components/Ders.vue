<template>
  <div class="hello">
    <button @click="addNewItem">Yukari Komponente MenuItemleri GOnder</button>
    {{ fullName }}
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    items: Array,
  },
  data() {
    return {
      message: "Merhaba",
      item: 1,
      firstName: "Ogur",
      lastName: "UYANIK",
      showMenu: true,
      debug: null,
      menuItems: [
        {
          id: 1,
          title: "Home",
          slug: "home",
        },
        {
          id: 2,
          title: "About",
          slug: "about",
        },
      ],
    };
  },
  methods: {
    addNewItem() {
      this.menuItems.push({
        id: 3,
        title: "Company",
        slug: "company",
      });
      this.$emit("emittedData", this.menuItems);
    },
  },
  mounted() {},
  created() {},
  watch: {
    "menuItems.length"(val) {
      if (val > 3) {
        this.menuItems = [];
      }
    },
  },
  computed: {
    fullName: function () {
      return this.firstName + " " + this.lastName;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
