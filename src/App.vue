<template lang="pug">
  #app
    header.bg-dark
      .container
        nav#nav.navbar.navbar-expand-lg.navbar-dark.px-0
          h1.font-weight-bold.navbar-brand Shoptime
          div.mr-auto
            ul.navbar-nav
              li.nav-item.active
                router-link.nav-link(to="/") HOME
              li.nav-item
                a.nav-link(@click.prevent="alert('coming soon')") ORDERS
              li.nav-item
                a.nav-link(@click.prevent="alert('coming soon')") PRODUCTS
          span.navbar-text.text-white ADMIN
    main
      router-view
</template>

<script>
export default {
  methods: {
    alert(message) {
      window.alert(message);
    }
  }
};
</script>


<style lang="scss">
@import "node_modules/bootstrap/scss/functions";
@import "./assets/scss/helpers/_variables";
@import "node_modules/bootstrap/scss/bootstrap";
// #app {
//   font-family: 'Avenir', Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }
#app {
  .lh-2 {
    line-height: 2rem;
  }
}

#nav {
  padding: 30px;
  margin-bottom: 30px;
  height: 70px;
  .navbar-brand {
    margin-right: 52px;
  }
  .nav-item .nav-link {
    padding: 23px 15px 19px;
    border-bottom: 4px solid black;
    margin: 0 5px;
  }
  .nav-item.active .nav-link {
    border-bottom: 4px solid white;
  }
  // a {
  //   font-weight: bold;
  //   color: #2c3e50;
  //   &.router-link-exact-active {
  //     color: #42b983;
  //   }
  // }
}
</style>
