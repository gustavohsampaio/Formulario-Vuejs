<template>
  <div class="mx-auto bg-blue-100" style="width: 600px">
    <div class="bg-blue-100 flex align-items-center border-bottom-1 surface-border surface-overlay w-full">
      <p class="text-2xl w-10 font-bold text-center">Cadastro de Desenvolvedor</p>
    </div>
    <div class="field col-12 md:col-12 bg-blue-100 my-3 flex align-items-center border-bottom-1 surface-border surface-overlay w-full">
      <p class="w-10 text-lg font-bold mr-3">Complete com suas informações:</p>
    </div>
    <div class="p-fluid mx-2 my-2 grid">
      <div class="field col-12 md:col-6">
        <label for="nome">Nome</label>
        <InputText id="nome" v-model="nome" type="text" :class="camposErros.indexOf('nome')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12 md:col-6">
        <label for="sobrenome">Sobrenome</label>
        <InputText id="sobrenome" v-model="sobrenome" type="text" :class="camposErros.indexOf('sobrenome')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12 md:col-8">
        <label for="email">E-mail</label>
        <InputText id="email" v-model="email" type="text" :class="camposErros.indexOf('email')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12 md:col-4">
        <label for="nascimento">Data de Nascimento</label>
        <Calendar id="nascimento" v-model="nascimento" :showIcon="true" :class="camposErros.indexOf('nascimento')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12">
        <label for="endereco">Endereço</label>
        <Textarea id="endereco" v-model="endereco" rows="1" :class="camposErros.indexOf('endereco')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12 md:col-4">
        <label for="estado">Estado</label>
        <Dropdown
          inputId="estado"
          v-model="SelecionarEstado"
          :options="estado"
          optionLabel="name"
          placeholder="Selecione"
          :class="camposErros.indexOf('estado')!=-1?'p-invalid':''"
        />
      </div>
      <div class="field col-12 md:col-4">
        <label for="cidade">Cidade</label>
        <InputText id="cidade" v-model="cidade" type="text" :class="camposErros.indexOf('cidade')!=-1?'p-invalid':''" />
      </div>
      <div class="field col-12 md:col-4">
        <label for="CEP">CEP</label>
        <InputText id="CEP" v-model="cep" type="text" :class="camposErros.indexOf('cep')!=-1?'p-invalid':''" />
      </div>
      <div class="col-12 md:col-12">
      <h6>Carreira de desenvolvedor</h6>
      </div>
      <div class="field-radiobutton col-12">
        <RadioButton id="dev1" name="dev" value="Front-end" v-model="dev" :class="camposErros.indexOf('dev')!=-1?'p-invalid':''"/>
        <label for="dev1">Front-end</label>
      </div>
      <div class="field-radiobutton col-12">
        <RadioButton id="dev2" name="dev" value="Back-end" v-model="dev" :class="camposErros.indexOf('dev')!=-1?'p-invalid':''"/>
        <label for="dev2">Back-end</label>
      </div>
      <div class="field-radiobutton col-12">
        <RadioButton id="dev3" name="dev" value="Fullstack" v-model="dev" :class="camposErros.indexOf('dev')!=-1?'p-invalid':''" />
        <label for="dev3">Fullstack</label>
      </div>
      <div class="field col-12 md:col-3">
        <label for="Senioridade">Senioridade</label>
        <Dropdown
          Id="senioridade"
          v-model="SelecionarSenioridade"
          :options="senioridade"
          optionLabel="name"
          placeholder="Selecione"
          :class="camposErros.indexOf('senioridade')!=-1?'p-invalid':''"
        />
      </div>
      <div class="col-12 md:col-12">
      <h6>Linguagens de Programação e Tecnologias</h6>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem1" value="JavaScript" v-model="linguagens"  :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem1">JavaScript</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem2" value="Java" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem2">Java</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem3" value="PHP" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem3">PHP</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem4" value="HTML" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem4">HTML</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem5" value="CSS" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem5">CSS</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem6" value="Vue.js" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem6">Vue.js</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem7" value="C#" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem7">C#</label>
      </div>
      <div class="field-checkbox col-12 md:col-3">
        <Checkbox id="linguagem8" value="Python" v-model="linguagens" :class="camposErros.indexOf('linguagens')!=-1?'p-invalid':''"/>
        <label for="linguagem8">Python</label>
      </div>
      
      <div class="field col-12">
        <label for="experiencia"> Conte sobre sua experiência </label>
        <Textarea id="experiencia" v-model="experiencia" rows="2"  :class="camposErros.indexOf('experiencia')!=-1?'p-invalid':''"/>
      </div>
      <div class="col-12 md:col-3 mx-auto mb-3">
      <Button @click="sucesso" label="Sucesso" class="bg-blue-500 border-blue-500 p-button-rounded"/>
      </div>
    </div>
  </div>
  <Toast position="top-right" />
</template> 

<script>
export default {
  name: "App",
  data() {
    return {
      
      nome: "",
      sobrenome: "",
      email: "",
      nascimento: "",
      endereco: "",

      SelecionarEstado: null,
        estado: [
          { name: "Acre" },
          { name: "Alagoas" },
          { name: "Amapá" },
          { name: "Amazonas" },
          { name: "Bahia" },
          { name: "Ceará" },
          { name: "Distrito Federal" },
          { name: "Espírito Santo" },
          { name: "Goiás" },
          { name: "Maranhão" },
          { name: "Mato Grosso" },
          { name: "Mato Grosso do Sul" },
          { name: "Minas Gerais" },
          { name: "Pará" },
          { name: "Paraíba" },
          { name: "Paraná" },
          { name: "Pernambuco" },
          { name: "Piauí" },
          { name: "Rio de Janeiro" },
          { name: "Rio Grande do Norte" },
          { name: "Rio Grande do Sul" },
          { name: "Rondônia" },
          { name: "Roraima" },
          { name: "Santa Catarina" },
          { name: "São Paulo" },
          { name: "Sergipe" },
          { name: "Tocantins" },
        ],

      cidade: "",
      cep: "",
      dev: "",

      SelecionarSenioridade: null,
      senioridade: [{ name: "Júnior" }, { name: "Pleno" }, { name: "Sênior" }],

      linguagens: [],
      experiencia:"",

      camposErros: [],

      
    };
  },
  methods: {
    sucesso: function() {
        this.camposErros = [];
        
        if(this.nome=="")
          this.camposErros.push("nome");
        
        if(this.sobrenome=="")
          this.camposErros.push("sobrenome");

          if(this.email=="")
          this.camposErros.push("email");

          if(this.nascimento=="")
          this.camposErros.push("nascimento");

          if(this.endereco=="")
          this.camposErros.push("endereco");

          if(this.SelecionarEstado==null)
          this.camposErros.push("estado");

          if(this.cidade=="")
          this.camposErros.push("cidade");

          if(this.cep=="")
          this.camposErros.push("cep");

          if(this.dev=="")
          this.camposErros.push("dev");

          if(this.SelecionarSenioridade==null)
          this.camposErros.push("senioridade");

          if(this.linguagens.length==0)
          this.camposErros.push("linguagens");

          if(this.experiencia=="")
          this.camposErros.push("experiencia");   

          if(this.camposErros.length>0)
          this.$toast.add({severity:'error', summary: 'Informações Inválidas', detail:'Preencha corretamente todas as informações!', life: 3000});
          
          else 
          this.$toast.add({severity:'success', summary: 'OK', detail:'Informações corretas!', life: 3000});
    }
  }
};
</script>

<style>
</style>
