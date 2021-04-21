<template>
  <div>
    <div class="layout sticky-header">
      <header c class="header sticky">
        <div c class="container">
          <div c class="left">
            <a
              href="/"
              aria-current="page"
              class="home-link active--exact active"
              ><img
                src="https://gridsome-forestry.netlify.app/assets/img/logo.332701b7.svg"
                alt="Nichlas W. Andersen"
                class="logo"
            /></a>
          </div>
          <nav c class="nav right">
            <g-link to="/post" class="nav__link">Journal</g-link>
            <g-link to="/contact" class="nav__link">Say Hi!</g-link>
          </nav>
        </div>
      </header>
      <slot />

      <footer c class="footer">
        <div c class="container">
          <span c>Copyright © 2021</span>
        </div>
      </footer>
    </div>
  </div>
</template>

<style>
</style>
