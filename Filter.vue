<template>
  <div class="row">
    <div class="col-12">
      <div>
        <select multiple v-model="filtro_value" @change="filtroMulti">
          <option value="1">Tipo 1</option>
          <option value="2">Tipo 2</option>
          <option value="3">Tipo 3</option>
        </select>
      </div>
      <table>
        <thead>
          <th>id</th>
          <th>name</th>
          <th>sport</th>
        </thead>
        <tbody>
          <tr v-for="item in dados" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.sport}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dados: [
        { id: 1, name: "Abby", sport: "basket", value: 1 },
        { id: 2, name: "Brooke", sport: "foot", value: 2 },
        { id: 3, name: "Courtenay", sport: "volley", value: 2 },
        { id: 4, name: "David", sport: "rugby", value: 3 }
      ],
      filtro_value: [],
      copia: [
        { id: 1, name: "Abby", sport: "basket", value: 1 },
        { id: 2, name: "Brooke", sport: "foot", value: 2 },
        { id: 3, name: "Courtenay", sport: "volley", value: 2 },
        { id: 4, name: "David", sport: "rugby", value: 3 }
      ]
    };
  },
  methods: {
    /*filtro() {
      //console.log(`@@@`,this.filtro_value)
      this.dados = this.copia;
      let dados = [];
      if (this.filtro_value.length === 1) {
        for (let i = 0; i < this.filtro_value.length; i++) {
          //console.log(`####`,this.filtro_value)
          dados[i] = this.dados.filter(
            filtro => filtro.value === parseInt(this.filtro_value[i])
          );
        }
        this.dados = dados[0];
        //console.log(`!!!`,dados)
      } else {
         let dados = [];
         let count = 0
          for (let x = 0; x < this.filtro_value.length; x++) {
          //console.log(`####`, this.filtro_value[x]);
          this.dados = this.copia
           dados[x] = this.dados.filter(
            filtro => filtro.value === parseInt(this.filtro_value[x])
          );
          //this.dados = dados.concat(this.filtro_value[x])
          console.log(`!@!@`,[].concat(...dados))
        //this.dados = [].concat(...dados)
          count++
        }
        //console.log(`!@!@`,dados,count)
        //this.dados = dados[0].concat(dados[1]).concat(dados[2]);
        this.dados = [].concat(...dados)
      }
    },*/
    filtroMulti() {
      this.dados = this.copia;
      let dados = [];
        for (let i = 0; i < this.filtro_value.length; i++) {
          dados[i] = this.dados.filter(
            filtro => filtro.value === parseInt(this.filtro_value[i])
          )
        }
       this.dados = [].concat(...dados)
    }
  }  
};
</script>
