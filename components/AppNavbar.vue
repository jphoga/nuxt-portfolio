<template>
  <header>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <NuxtLink class="nav-link" to="/">Home</NuxtLink>
          <NuxtLink class="nav-link" to="/about">About</NuxtLink>
          <NuxtLink class="nav-link" to="/blog">Blog</NuxtLink>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown id="lang-item" text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss">
.nav-link {
  color: rgba(1, 1, 1, 0.5) !important;
  font-size: 1.25rem;
}

header {
  margin: 0 7rem;
  height: 4rem;
}
.bg-info {
  background-color: transparent !important;
}

#nav-collapse {
  margin-top: 2px;
}
</style>
