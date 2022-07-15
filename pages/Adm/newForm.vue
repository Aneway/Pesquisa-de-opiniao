<template>
  <div>
    <div id="supergraphic"></div>
    <header>
      <div class="header_logo">
          <img class="logo" src="@/static/logoBosch.svg"/>
      </div>
    </header>
    <main>  
      <div class="main_content">
        <div class="edit_form">
          <span>Nome do Formuário</span>
          <br></br>
          <InputText class="inputNameForm" type="text" placeholder="Este aqui é o nome do formulário"/>
          <Divider/>

          <span>Tipo de Formulário </span>
          <br></br>
          <div class="identify">
            <label><RadioButton value="Identificável" v-model="identify"/> Identificável</label>
            <label><RadioButton value="Não Identificável" v-model="identify"/> Não Identificável</label>
          </div>
          <Divider/>

          <div  v-for="questions,index of allQuestions">
            <div class="questionType">
              <span>Pergunta {{index + 1}}</span>
              <Dropdown class="dropdown_type" v-model="questions.dropBox" :options="types" optionLabel="name" placeholder="Tipo da Pergunta"/>
            </div>
            
            <br><Textarea v-model="questions.field" class="questionTextArea" rows="5" cols="30" placeholder="Este aqui é o enunciado da pergunta"/>
            <br>
            <InputText class="optionsQuestion" v-if="questions.dropBox.name=='Escolha única'" v-model="questions.aux" placeholder="Adicionar opção"></InputText>
            <Button v-if="questions.dropBox.name=='Escolha única'" @click="addUnic(questions.escolhaUnica, questions.aux, index)">+</Button>

            <div v-for="category,index of questions.escolhaUnica">
              <br>
              <RadioButton v-if="questions.dropBox.name=='Escolha única'" :id="category.key" name="question" :value="escolhaUnica.question" />
              <Button class="btnRemoveQuestion"v-if="questions.dropBox.name=='Escolha única'" @click="removeUnic(index, questions.escolhaUnica, questions.aux)">x</Button>
              <label v-if="questions.dropBox.name=='Escolha única'" for="category.key">{{category.question}}</label>
            </div>
            <br>
            <Divider/>
          </div>
          <Button label="Nova Pergunta" icon="pi pi-plus" class="p-button-text" @click="addQuestion()"/>
        </div>
        <button class="btn_Salvar">FINALIZAR E SALVAR</button>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
		return {
			identify: null,
      value:'',
      selectedType: {name:null},
		  types: [
			{name: 'Discursiva'},
      {name: 'Quantitativa'},
			{name: 'Escolha única'},
      {name: 'Múltipla Escolha'}
		  ],
      discursiva: [
        {texto:null}
      ],
      quantitativa: [{
        sempre:false,
        muitasVezes: false,
        asVezes:false,
        algumasVezes: false,
        poucasVezes: false,
        nunca: false,
        }
      ],
      escolhaUnica: [],
      multiplaEscolha:[{}],
      valueUnic:'',
      allQuestions:[{dropBox: "", field: "", escolhaUnica: [], aux: ""}]
      }
		},

    methods: {
      // c = escolha unica
      addUnic(c, aux, index){
        c.push({question:aux})
      this.allQuestions[index].aux = ''

      },
      removeUnic(index, c, aux){
        c.splice(index,1)
      },

      addQuestion(){
        this.allQuestions.push({dropBox: "", field: "", escolhaUnica: [], aux: ""})
	    },
	  }
}
</script>

<style lang="scss" scoped>

*{
  font-family: 'BoschSans-Regular';
}

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
  background-color: var(--gray_light);
  height: 89vh;
  display: flex;
  align-items: center;
  justify-content: center;

  .main_content{
    .btn_Salvar{
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

      &:hover{
        cursor: pointer;

      }
      &:active {
        position:relative;
        background-color: var(--red_dark);
      }
    }

    .edit_form{
      background: var(--white_absolute);
      height: 500px;
      width: 850px;
      border-radius: 6px;
      box-sizing: border-box; //para criar uma borda interna
      padding: 30px; //tamanho da borda interna
      overflow-y:scroll;

      .questionTextArea{
        width: 500px;
        height: 50px;
      }
      .inputNameForm{
        width: 400px;
        height: 40px;
      }
      span{
        font-size: 17px;
      }
      .identify{
        display: flex;
        align-items: center;
        justify-content: space-evenly;
      }
      .btnRemoveQuestion{
        background-color: var(--red_default);
        border-radius:20px;
        border-color: var(--red_default);
        width: 20px;
        height: 20px;
        display:inline-block;
        cursor:pointer;
        font-size:13px;
        padding: 0.5px 1px;

      }
      .dropdown_type{
        height: 40px;
        background-color: var(--gray_super_light);
      }
      .questionType{
        display: flex;
        align-items: center;
        justify-content: space-between;
      }
      .optionsQuestion{
        width: 150px;
      }
    }
  }
}


</style>
