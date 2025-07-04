<template>
  <div id="app" :class="{'dark-mode': darkmode}">
    <form class="form-container" @submit.prevent="onSubmit">
      <div class="form-group">
        <label for="name">Nome:</label>
        <input id="name" v-model="name" placeholder="Escreva seu nome" :class="{'input-warning': name.trim() === ''}" />
      </div>
      <div class="form-group">
        <label for="age">Idade:</label>
        <input id="age" v-model.number="age" placeholder="Escreva sua idade" :class="{'input-warning': age === null || age === '' || isNaN(age)}" />
      </div>
      <div class="form-group">
        <label for="email">Email:</label>
        <input id="email" v-model.trim="email" placeholder="Escreva seu email" :class="{'input-error': !isEmailValid}" />
        <div v-if="email && !isEmailValid" class="input-error">Informe um e-mail válido, sem espaços.</div>
      </div>
      <div class="form-group">
        <label for="cep">CEP:</label>
        <input id="cep" v-model.trim="cep" placeholder="00000-000" :class="{'input-error': !isCepValid}" @input="formatarCep" @blur="buscarCEP"/>
        <div v-if="cep && !isCepValid" class="input-error">Informe um CEP válido.</div>
        <div v-if="address" class="input-CEP">{{ address }}</div>
      </div>
      <div class="form-group">
        <label for="selectedOption">Cor favorita:</label>
        <select id="selectedOption" v-model="selectedOption" :class="{'input-warning': selectedOption === ''}">
          <option v-for="item in options" :key="item" :value="item">{{ item }}</option>
        </select>
      </div>
      <div class="form-group hobbies-group">
        <span class="hobbies-label">Hobbies:</span>
        <label for="hobGames" class="label-small">Games:</label>
        <input id="hobGames" type="checkbox" v-model="hobGames" />
        <label for="hobRead" class="label-small">Leitura:</label>
        <input id="hobRead" type="checkbox" v-model="hobRead" />
        <label for="hobProgramming" class="label-small">Programação:</label>
        <input id="hobProgramming" type="checkbox" v-model="hobProgramming" />
      </div>
      <div class="form-group">
        <label for="history">História:</label>
        <textarea id="history" v-model="history" placeholder="Escreva sua história" :class="{'input-warning': history.trim() === ''}"></textarea>
      </div>
      <div class="form-group checkbox-group">
        <label for="isActive">Ativo:
          <input id="isActive" type="checkbox" v-model="isActive" :disabled="!canActivate" />
        </label>
      </div>
      <div v-if="!canActivate" class="alert-warning">
        Preencha todos os campos obrigatórios para ativar o perfil.
      </div>
      <button type="submit">Enviar</button>
      <button type="button" class="btn-darkmode" @click="darkmode = !darkmode">
        {{ darkmode ? 'Tema Claro' : 'Tema Escuro' }}
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      name: '',
      age: null,
      email: '',
      cep: '',
      isActive: false,
      options: ['laranja', 'verde', 'azul', 'vermelho'],
      selectedOption: '',
      history: '',
      hobGames: false,
      hobRead: false,
      hobProgramming: false,
      address: '',
      darkmode: false
    };
  },
  computed: {
    canActivate() {
      return (
        this.name.trim() !== '' &&
        this.age !== null && this.age !== '' && !isNaN(this.age) &&
        this.isEmailValid &&
        this.isCepValid &&
        this.selectedOption !== '' &&
        this.history.trim() !== '' &&
        (this.hobGames || this.hobRead || this.hobProgramming) &&
        //this.isActive !== false &&
        this.address.trim() !== ''
      );
    },
    isEmailValid() {
      const email = this.email.trim();
      // Regex simples para validar e-mail
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return email !== '' && emailRegex.test(email);
    },
    isCepValid() {
      const cep = this.cep.trim();
      // Regex simples para validar CEP no formato 00000-000
      const cepRegex = /^\d{5}-\d{3}$/;
      return cep !== '' && cepRegex.test(cep);
    }
  },
  methods:{
    onSubmit(){
      if (this.canActivate) {
        alert('Perfil ativado com sucesso!');
        this.name = '';
        this.age = null;
        this.email = '';
        this.cep = '';
        this.selectedOption = '';
        this.history = '';
        this.hobGames = false;
        this.hobRead = false;
        this.hobProgramming = false;
        this.address = '';
        this.isActive = false;
      } else {
        alert('Preencha todos os campos obrigatórios.');
      }
    },
    formatarCep(event) {
      let v = event.target.value.replace(/\D/g, ''); // Remove tudo que não for dígito
      if (v.length > 5) v = v.replace(/^(\d{5})(\d)/, '$1-$2');
      this.cep = v;
    },
    async buscarCEP(){
      if (this.isCepValid) {
        try{
          const response = await fetch(`https://viacep.com.br/ws/${this.cep}/json/`);
          if (!response.ok) {
            throw new Error('Erro ao buscar CEP');
          } else {
            const data = await response.json();
            if (data.erro) {
              throw new Error('CEP não encontrado');
            } else {
              this.address = `End.: ${data.logradouro}, Cidade: ${data.localidade}, Estado: ${data.uf}`;
            }
          }
        } catch (error) {
          console.error(error);
        }
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.label-small {
  font-size: smaller;
  font-weight: 500;
}
.form-container {
  display: inline-block;
  text-align: left;
  background: #fff;
  padding: 32px 40px;
  border-radius: 12px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.08);
  width: 400px;
}
.form-group {
  margin-bottom: 18px;
}
.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
}
.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 8px 10px;
  border: 1.5px solid #409eff;
  border-radius: 4px;
  font-size: 1em;
  box-sizing: border-box;
}
.checkbox-group {
  display: flex;
  align-items: center;
}
.checkbox-group label {
  margin-bottom: 0;
  margin-right: 8px;
  font-size: smaller;
  display: inline-flex;
}
.hobbies-group {
  border: 1px solid #bdbdbd;
  border-radius: 6px;
  padding: 12px 10px 6px 10px;
  margin-bottom: 18px;
  background: #fafbfc;
  display: flex;
  align-items: center;
  gap: 10px;
}
.hobbies-label {
  font-weight: 600;
  margin-right: 12px;
  font-size: smaller;
}
button[type="submit"],
button[type="button"].btn-darkmode {
  background: #2c3e50;
  color: #fff;
  border: none;
  padding: 10px 24px;
  border-radius: 4px;
  font-size: 1em;
  cursor: pointer;
  margin-top: 10px;
  transition: background 0.2s;
}
button[type="submit"]:hover,
button[type="button"].btn-darkmode:hover {
  background: #1a232c;
}
.alert-warning {
  background: #fffbe6;
  color: #856404;
  border: 1px solid #ffe58f;
  border-radius: 4px;
  padding: 10px 14px;
  margin-bottom: 16px;
  font-size: 0.98em;
  display: block;
}
.input-warning {
  border: 1.5px solid #ffc107 !important;
  background: #fffbe6;
}
.input-error {
  color: #fa1d00;
  background: #ffede6;
  border: 1.5px solid #fa1d00 !important;
  border-radius: 4px;
  padding: 6px 10px;
  margin-top: 6px;
  font-size: 0.95em;
}
.input-CEP {
  color: #fa1d00;
  background: #ffede6;
  border: 1.5px solid #fa1d00 !important;
  border-radius: 4px;
  padding: 6px 10px;
  margin-top: 6px;
  font-size: 0.95em;
}
.dark-mode {
  background-color: #121212 !important;
  color: #e0e0e0 !important;
}
.dark-mode .form-container {
  background: #1e1e1e !important;
  box-shadow: 0 2px 16px rgba(0,0,0,0.25) !important;
}
.dark-mode input,
.dark-mode select,
.dark-mode textarea {
  background: #2a2a2a !important;
  color: #e0e0e0 !important;
  border: 1.5px solid #444 !important;
}
</style>