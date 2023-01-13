<template>
  <v-container>
    <v-row>
      <v-col>
        <h2>Llista de Persones</h2>
        <v-card v-for="(persona, i) in filteredPeople" :key="persona[i]">
          <h3>{{ persona.nom }}</h3>
          <br />
          <h4>{{ persona.edat }}</h4>
        </v-card>
      </v-col>
      <v-col
        ><h2>Llista d'accions</h2>
        <v-btn @click="OrdenarAZ()">Ordenar A-Z</v-btn>
        <v-btn @click="OrdenarZA()">Ordenar Z-A</v-btn>
        <br />
        <v-text-field v-model="searchQuery" label="Search"></v-text-field><br />
        <v-btn @click="personaElMesGran()">Persona el Mes Gran</v-btn>
        <h2>{{ personaElMesGran.nom }}</h2>
        <div class="hover:shadow">
        <h2>Mise a jours de css</h2>
        <v-img style="width:50vh; height:50vh" src="https://images.unsplash.com/photo-1668112055980-bca362d15815?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=415&q=80"></v-img>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      elMesGran: -10,
      searchQuery: "",
      persones: [
        { nom: "David", edat: 25 },
        { nom: "Hicham", edat: 31 },
        { nom: "Pere", edat: 27 },
        { nom: "Laura", edat: 42 },
        { nom: "Isabel", edat: 35 },
        { nom: "Joan", edat: 37 },
        { nom: "Kamal", edat: 52 },
        { nom: "Noura", edat: 21 },
      ],
    };
  },
  methods: {
    OrdenarAZ() {
      this.persones.sort((a, b) => (a.nom > b.nom ? 1 : -1));
    },
    OrdenarZA() {
      this.persones.sort((a, b) => (a.nom > b.nom ? -1 : 1));
    },
    personaElMesGran() {
      this.persones.sort((a, b) => b.edat - a.edat)
      return console.log("La persona mes gran es",this.persones[0].nom, " y te ", this.persones[0].edat, " anys")
      
      }
    },
  
  computed: {
    filteredPeople() {
      return this.persones.filter((persona) => {
        return (
          persona.nom.toLowerCase().indexOf(this.searchQuery.toLowerCase()) !==
          -1
        );
      });
    },
    /* personaElMesGran() {
      let self = this;
      console.log(self.filteredPeople);
      return self.filteredPeople.reduce((a, b) => {
        return a.edat > b.edat ? a : b;
      })
     console.log()
    }*/
  },
};
</script>

<style lang="scss" scoped></style>
