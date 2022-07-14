<template>
  <div>
    <div id="supergraphic"></div>
    <header>
      <div class="header_logo">
          <img class="logo" src="@/static/logoBosch.svg"/>
      </div>
    </header>
    <main>
      
      <div class="edit_form">
        <span>Nome do Formuário</span>
        <input></input>
        <Divider/>
        <span>Tipo de Formulário: </span>
        <RadioButton name="identify" value="Identificável" v-model="identify" />
        <label>Identificável</label>
        <RadioButton name="identify" value="Não Identificável" v-model="identify" />
        <label>Não Identificável</label>
        <Divider/>
        <!-- <div v-for="(item,index) in questions"> -->
        <div  v-for="questions,index of aaaa">

          <!-- <Dropdown v-model="selectedCity" :options="cities" optionLabel="name" placeholder="Select a City" /> -->
          <span>Pergunta </span>
          <br></br><Dropdown v-model="selectedType" :options="types" optionLabel="name" placeholder="Tipo da Pergunta"/>
          <br></br><Textarea v-model="value" class="questionTextArea" rows="5" cols="30" placeholder="Este aqui é o enunciado da pergunta"/>
          <br></br>
          <InputText v-if="selectedType.name=='Escolha única'" v-model="valueUnic"></InputText>
          <Button v-if="selectedType.name=='Escolha única'" @click="addUnic">+</Button>
          <div v-for="category,index of escolhaUnica">
            <RadioButton v-if="selectedType.name=='Escolha única'" :id="category.key" name="question" :value="escolhaUnica.question" />
            <label v-if="selectedType.name=='Escolha única'" for="category.key">{{category.question}}</label>
            <Button v-if="selectedType.name=='Escolha única'" @click="removeUnic(index)">x</Button>
          </div>
        
          
          
          
          <Divider/>
        </div>
        
        
        <Button label="Nova Pergunta" icon="pi pi-plus" class="p-button-text" @click="addQuestion()"/>

      </div>
      <!-- <Button label="Finalizar e Salvar"></Button> -->
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
      aaaa:[]
      }
		},

    methods: {
      addUnic(){
        this.escolhaUnica.push({question:this.valueUnic})
        this.valueUnic = ''
      },
      removeUnic(index){
        this.escolhaUnica.splice(index,1)
        this.valueUnic = ''
      },

      addQuestion(){
        this.aaaa.push({questions:this.plusQuestions})
        this.allQuestions = ''
	    }
      

      
	}
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
  background-color: var(--gray_light);
  height: 89vh;
  display: flex;
  align-items: center;
  justify-content: center;

  .edit_form{
    background: var(--white_absolute);
    height: 500px;
    width: 850px;
    border-radius: 6px;
    box-sizing: border-box; //para criar uma borda interna
    padding: 30px; //tamanho da borda interna
    overflow-y:scroll;

    .questionTextArea{
      width: 550px;
      height: 50px;

    }
  }
}


</style>
