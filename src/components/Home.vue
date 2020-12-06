<template>
  <div>
    <div class="center bg-green">
      <h1 id="logo">
        conduit
      </h1>
      <p id="lead">
        Um lugar para você compartilhar todo o seu conhecimento!
      </p>
    </div>
    <div class="center">
      <div class="row sm-vertical">
        <div class="col sm-full">
          <nav>
            <router-link :to="{ name: 'my-feed' }">
              Meu feed
            </router-link>
            <router-link :to="{ name: 'global-feed' }">
              Global feed
            </router-link>
          </nav>
          <main>
            <router-view />
          </main>
        </div>
        <aside
          class="no-flex sm-full"
          style="width: 260px;"
        >
          Tags populares
        </aside>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
  .bg-green {
    padding: 2em;
    color: white;
    background-color: #5cb85c;
  }
  #logo {
    font-family: 'Courier New', Courier, monospace;
    font-size: 3em;
    text-shadow: 0 1px 3px #0000004b;
  }
  #lead {
    font-size: 1.2em;
    font-size: Arial, Helvetica, sans-serif;
  }
</style>
