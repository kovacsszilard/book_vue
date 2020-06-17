<template>
  <tr v-if="!isUpdate">
    <th scope="row">{{ index }}</th>
    <td>{{ tableItem.title }}</td>
    <td>{{ tableItem.author }}</td>
    <td>{{ tableItem.category_id }}</td>    
    <td>{{ tableItem.piece }}</td>
    <td>
      <button @click="deleteItem(index)" type="button" class="btn btn-danger">
        Törlés
      </button>
    </td>
    <td v-if="!isUpdate">
      <button
        @click="isUpdate = !isUpdate"
        type="button"
        class="btn btn-success"
      >
        Módosítás
      </button>
    </td>
    <td v-if="isUpdate">
      <button type="button" class="btn btn-primary">Ment</button>
    </td>
  </tr>
  <tr v-else>
    <th scope="row">{{ index }}</th>
   <td>
      <input type="text" v-model="tableItem.title" class="form-control" />
  </td>


     <td>
      <input type="text" v-model="tableItem.author" class="form-control" />
    </td>
    
    <td><input type="number" v-model.number="tableItem.category_id" class="form-control" /></td>
     <!--<td><input type="number" v-model.number="tableItem.isbn" class="form-control" /></td>-->
      <td><input type="number" v-model.number="tableItem.piece" class="form-control" /></td>
  
    <td>
      <button @click="deleteItem(index)" type="button" class="btn btn-danger">Törlés</button>
    </td>

    <td v-if="!isUpdate">
      <button
        @click="isUpdate = !isUpdate"
        type="button"
        class="btn btn-success">Ment</button>
    </td>

    <td v-if="isUpdate">
            <!--<button :disabled="tableItem.cim.length < 3" @click="submit(index)" type="button" class="btn btn-primary" >-->
            <button @click="submit(index)" type="button" class="btn btn-primary" >
        Ment
      </button>
    </td>
  </tr>  
</template>

<script>
import axios from 'axios';
export default {
  name: "TableRow",
  data() {
    return {
      isUpdate: false,
    };
  },
  props: {
    index: Number,
    tableItem: Object,
    tableItems: Array
    
  },
  methods: {
   deleteItem(id) {
      this.tableItems.splice(id, 1);
      this.tableItems.delete(this.tableItem);
      axios.delete("http://localhost:8000/api/book/",this.tableItem.id)
    },
    submit(id) {
      this.tableItems[id] = this.tableItem;
      this.isUpdate = false;
    },
    
  },
};
</script>