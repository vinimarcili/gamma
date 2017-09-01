<template>
  <div id="app" class="default-font">
    <figure>
      <img src="./assets/images/logo.png" alt="Gamma" title="Gamma" class="img-responsive">
    </figure>
    <router-view></router-view>
    <footer>
      <a href="mailto:vinipetter@gmail.com">Developed By Vinicius Marcili</a>
      <a href="mailto:saragarcia.gr@gmail.com">Base Design By Sara Garcia</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
$transition: all 0.3s ease;

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 50px 0 15px;
  background: rgba(0, 0, 0, 0.9);
  figure{
    max-width: 300px;
    display: inline-block;
    margin: 0 auto;
  }
  footer {
    a {
      display: block;
      color: #fff;
      transition: $transition;
      font-size: 15px;
      &:hover {
        text-decoration: none;
        font-size: 17px;
      }
    }
  }
}
</style>
