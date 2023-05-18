<template>
  <div class="body">

    <div class="card">
      <span class="title">
        <h1>Anotações</h1>
      </span>

      <div class="card2">
        <span class="title2">
          <h2>Título:</h2>
          <input class="text" type="text" placeholder="Insira o título da anotaçaõ" v-model="name">
        </span>

        <span class="description">
          <h2>Descrição:</h2>
          <input class="elementsDescription" type="textarea" placeholder="Descreva a anotaçaõ" v-model="descrição">
        </span>

        <span class="date">
          <h2>Data:</h2>
          <input class="dateAt" type="date" required autofocus placeholder="Adicione a data" v-model="data">
        </span>

        <div class="add">
          <button class="buttonAdd" v-on:click="addNotes" type="submit">Adicionar</button>
        </div>
      </div>

      <!-- <div class="img">
        <img src="@/assets/note.jpg" />
      </div> -->

      <span class="bgResults">
        <div class="results" v-for="(i, index) in allNotes" :key="i.allNotes">
          <h3>Título: <span class="resultTitle">{{ i.name }}</span></h3>
          <h3>Descrição: <span class="resultDescription">{{ i.descrição }}</span></h3>
          <h3>Data: <span class="resultDescription">{{ (i.data) }}</span></h3>

          <div class="delet">
            <button class="buttonDelet" v-on:click="deletNotes(index)" type="submit"> Deletar</button>
          </div>
        </div>
      </span>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      coments: [],
      name: '',
      descrição: '',
      data: ''
    }
  },
  methods: {
    addNotes() {
      if (this.descrição.trim() === '') {
        return;
      }
      this.coments.push({
        name: this.name,
        descrição: this.descrição,
        data: this.data
      });

      this.name = '';
      this.descrição = '';
      this.data = '';
    },
    deletNotes(index) {
      this.coments.splice(index, 1);
    },
  },
  computed: {
    allNotes() {
      return this.coments.map(i => ({
        ...i,
        name: i.name.trim() === '' ? 'Anônimo' : i.name,

        data: i.data.trim() === '' ? '00/00/0000' : i.data


      }))
    },
  }
}

</script>

<style>
body {
  background: #d3d3d3;

}

input {
  color: #02273a;
  padding: 0 10px;

}


.card {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  position: relative;
  flex-direction: row;
  min-width: 0;
  background: #054f77;
  word-wrap: break-word;
  background-clip: border-box;
  border-radius: .8rem;
  padding: 0 0 150px;
  /*  */
  top: 20px;
  max-width: 100%;
  min-height: 480px;
}

.card {
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  margin: 1em;
  padding: 1em;
}

h2,
h3 {
  color: #f2eee3;
}

.elementsDescription {
  display: inline-flex;
  gap: 1rem;
}

.date,
.description,
.title2 {
  display: flex;
  padding: 0 30px;
  gap: 10px;
}

.elementsDescription,
.text {
  border-radius: 10px;
  height: 35px;
    width: 5rem;
  align-self: center;
}

.dateAt {
  border-radius: 10px;
  height: 35px;
  width: 150px;
  align-self: center;
}

::placeholder {
  padding: 0 10px;
  color: #02273a;
}

button {
  border-radius: 20px;
  border: 1px solid #F2eee3;
  background-color: #F2eee3;
  color: black;
  font-size: 12px;
  font-weight: bold;
  padding: 12px 45px;
  letter-spacing: 1px;
  text-transform: uppercase;
  transition: transform 80ms ease-in;
  border-color: black;
}

button:hover {
  border: 2px solid white;
  box-shadow: white 0px 0px 12px 1px inset, white 0px 0px 12px 1px;
  border-radius: 15px;
}

.add {
  display: flex;
  justify-content: center;
  padding-top: 20px;
}

.buttonAdd {
  cursor: pointer;
  display: flex;
  border-radius: 5px;
  height: 30px;
  align-items: center;
  padding: 0 40px;
}

.delet {
  display: flex;
  justify-content: center;
}

.buttonDelet {
  cursor: pointer;
  display: flex;
  border-radius: 5px;
  height: 30px;
  align-items: center;
  padding: 0 45px;
}

.bgResults {
  display: block;
  padding-left: 0.1vmax;
  padding-top: 30px;
}

.results {
  display: block;
  background: rgb(60, 114, 134);
  border: 20px;
  padding: 30px;
  justify-content: center;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  margin: 1em;
  padding: 1em;
}

.resultTitle,
.resultDescription {
  color: #031822;
  font-weight: bold
}

/*  */
@media screen and (min-width: 1024px) {

  /*  */
  body {

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;

  }

  .card {
    width: 768px;

  }

}
</style>
