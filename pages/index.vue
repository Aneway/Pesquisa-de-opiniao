<template>
  <div>
    <div id="supergraphic"></div>
    <header>
      <div class="header_logo">
          <img class="logo" src="@/static/logoBosch.svg"/>  
      </div>
    </header>
    <main>
      <div class="login">
        <h3 class="title">Login</h3>
        <form>
          <div class="single-input">
              <input type="text" class="input" required>
              <label>EDV</label>
          </div>
          <div class="single-input">
              <input type="password" class="input" required>
              <label>Senha</label>
          </div>
          <button class="btn_login">ENTRAR</button>
      </form>

        <!-- <NuxtLink to="/adm">
          adm
        </NuxtLink>
        
        <a href="/adm">teste</a>

         <button v-on:click="$router.push(/adm)"/>-->
        

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
    box-shadow: 0px 3px 5px var(--gray_shadow);
  }
  .logo{
    height: 100%;
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
}

main{
  background-color: var(--gray_light);
  height: 89vh;
  display: flex;
  align-items: center;
  justify-content: center;
  // to floating input
  
  

  .login{
    background: var(--white_absolute);
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    box-shadow: 0px;
    height: 330px;
    width: 300px;
    box-sizing: border-box; //para criar uma borda interna
    padding: 40px; //tamanho da borda interna
    //display: flex;
    //align-items: center;
    //justify-content: center;
  }

  form{
      width: 100%;
      max-width: 350px;
      padding: 2%;

      .title{
        font-size: 100px;
      }

      .single-input{
        position: relative;
        margin: 30px 0;
      }
      .single-input label{
          position: absolute;
          bottom: 5px;
          left: 0;
          color: #808080;
          cursor: text;
          transition: 0.5s ease-in-out;
      }

      .input{
          width: 100%;
          padding: 5px;
          border: 0;
          border-bottom: 2px solid rgb(200,200,200);
          outline: 0;
          font-size: 16px;
          color: rgb(80,80,80);
          transition: 0.5s ease-in-out;
      }

      .input:focus,
      .input:valid{
          border-bottom: 2px solid cornflowerblue;
      }
      .input:focus ~ label,
      .input:valid ~ label{
          transform: translateY(-24px);
          font-size: 12px;
          color: cornflowerblue;
      }

      .btn_login{
        background-color: #e61919; 
        border: none;
        color: white;
        text-align: center;
        font-size: 12px;
        font-weight: bold;
        width: 161px;
        height: 32px;
        margin-top: 40px;
        //alinhar
        display: block;
        margin-left: auto;
        margin-right: auto;

        &:hover{
          cursor: pointer;

        }
        &:active {
          position:relative;
          background-color: var(--red_dark);
        }
      }
    }  
  }

</style>
