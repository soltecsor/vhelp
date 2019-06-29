<template>
  <div class="row">
    <div class="col-8">
      <h3>Draggable table</h3>

      <table class="table table-striped">
        <thead class="thead-dark">
          <draggable 
            v-model="headers"                                                                                                                                                   
            tag="tr" 
            :move="checkMove"
            >
            <th v-for="header in headers"
                :key="header" 
                scope="col"
                @drop="dragging = true"    
                @mousemove="dragging = false" 
                @mouseleave="gravaColuna"
        
            >
            {{ header }}
            </th>
          </draggable>
        </thead>
        <tbody>
          <tr v-for="item in list" :key="item.name">
            <td v-for="header in headers" :key="header">{{ item[header] }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "table-column-example",
  display: "Table Column",
  order: 9,
  components: {
    draggable
  },
  data() {
    return {
      headers: ["id", "name", "sport"],
      list: [
        { id: 1, name: "Abby", sport: "basket" },
        { id: 2, name: "Brooke", sport: "foot" },
        { id: 3, name: "Courtenay", sport: "volley" },
        { id: 4, name: "David", sport: "rugby" }
      ],
      dragging: false,
      position:null
    };
  },
  methods:{
    checkMove(e) {
        this.dragging = false
        this.position = e.draggedContext.futureIndex

    },
    gravaColuna(){
       if(this.dragging){
            console.log(`gravando coluna...`, this.position)
        }
    }
  },
 }  
</script>
<style scoped> 
.buttons {
  margin-top: 35px;
}
</style>