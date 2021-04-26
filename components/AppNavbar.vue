<template>
  <header>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">Home</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">About</b-nav-item>
          <b-nav-item href="#">Blog</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">日本語</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
header {
  margin: 0 8rem;
  height: 4rem;
}
.bg-info {
  background-color: transparent !important;
}

#nav-collapse {
  margin-top: 2px;
}
</style>
