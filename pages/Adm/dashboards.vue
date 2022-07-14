<template>
  <div>
    <div id="supergraphic"></div>
    <header>
      <div class="header_logo">
          <img class="logo" src="@/static/logoBosch.svg"/>
      </div>
    </header>

    <main>
      <h3>Resultados - Pesquisa de Opinião</h3>

      <div>
        
      </div>

    </main>

    <footer></footer>

  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style lang="scss" scoped>

#supergraphic{
  background-image: url("@/static/supergraphic.svg");
  background-size: cover;
  height: 1vh;
  width: 100%;
}

header{
  .header_logo{
    height: 10vh;
    width: 100%;
    box-shadow: 0px 1px 5px var(--gray_shadow);
  }
  .logo{
    height: 100%;
  }
}

main{
  height: 89vh;
  display: flex;
  align-items: center;
  justify-content: center;

}


</style>
