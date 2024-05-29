<script setup>
</script>

<template>
 <nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://img.freepik.com/darmowe-wektory/ptak-kolorowe-logo-wektor-gradientu_343694-1365.jpg?size=338&ext=jpg&ga=GA1.1.632798143.1713571200&semt=ais" height="112">
    </a>

    <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>

  <div id="navbarBasicExample" class="navbar-menu">

    
    
    <div class="navbar-start">
      <NuxtLink to="/" class="navbar-item">
        Home
      </NuxtLink>

      <NuxtLink to="/about" class="navbar-item">
        about
      </NuxtLink>

      <a href="/about" class="navbar-item">
        about (nie spa)
      </a>

      <div class="navbar-item has-dropdown is-hoverable">
        <a class="navbar-link">
          More
        </a>


        <div class="navbar-dropdown">
          <a class="navbar-item">
            About
          </a>
          <a class="navbar-item">
            Jobs
          </a>
          <a class="navbar-item">
            Contact
          </a>
          <hr class="navbar-divider">
          <a class="navbar-item">
            Report an issue
          </a>
        </div>
      </div>
    </div>
   
    <div class="content has-text-centered">
    <p>
      Prace wykonali: Szymon Fierek i Jakub Mazur
    </p>
  </div>

    <div class="navbar-end">
      <div class="navbar-item">
        <div class="buttons">
          <a class="button is-primary">
            <strong>Sign up</strong>
          </a>
          <a class="button is-light">
            Log in
          </a>
        </div>
      </div>
    </div>
  </div>
</nav>

</template>

<style scoped lang="scss">
.navbar {
  background-color: #f8f9fa;
  padding: 0.5rem 1rem;
  border-bottom: 2px solid #eaeaea;

  .navbar-item {
    font-size: 1.1rem;
    color: #343a40;
    &:hover {
      background-color: #e9ecef;
      color: #007bff;
    }
  }

  .navbar-link {
    font-weight: bold;
    color: #343a40;
    &:hover {
      color: #007bff;
    }
  }

  .navbar-dropdown {
    background-color: #f8f9fa;
    .navbar-item {
      color: #343a40;
      &:hover {
        background-color: #e9ecef;
        color: #007bff;
      }
    }
  }

  .navbar-burger {
    color: #343a40;
    &:hover {
      color: #007bff;
    }
  }

  .buttons .button {
    margin-left: 0.5rem;
  }

  .button.is-primary {
    background-color: #007bff;
    border-color: #007bff;
    &:hover {
      background-color: #0056b3;
      border-color: #004085;
    }
  }

  .button.is-light {
    background-color: #f8f9fa;
    border-color: #f8f9fa;
    color: #343a40;
    &:hover {
      background-color: #e9ecef;
      border-color: #dae0e5;
    }
  }
}
</style>
