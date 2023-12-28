<template>
  <div class="bg-secondary sticky-top">
    <b-navbar toggleable="lg" class="container">
      <b-navbar-brand href="#">Shooping</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav class="justify-content-between">
        <b-navbar-nav>
          <li class="nav-item">
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/galery">Galery</router-link>
          </li>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
            <li class="nav-item">
              <router-link class="nav-link" to="/keranjang">
                <b-icon-bag></b-icon-bag>
                <span class="badge bg-primary rounded-circle">0</span>
              </router-link>
            </li>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>