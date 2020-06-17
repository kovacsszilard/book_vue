<template>
  <div>
     <div class="row">
          <div class="col-9">            
            <hr>
    <div style = "height:300px; overflow-y:scroll">

    
    <table  class="table table-bordered table-dark">
      <thead>
        <tr>
          <th scope="col">Azon</th>
          <th scope="col">Cím</th>
          <th scope="col">Szerző</th>
          <th scope="col">Kategória</th>
         
          <th scope="col">Példányszám</th>
        </tr>
      </thead>
      <tbody>

        <table-row
          v-for="(tableItem, index) in tableItems"
          :key="index"
          :tableItem="tableItem"
          :index="index"
          :tableItems="tableItems"
        ></table-row>
      </tbody>
    </table>
    </div>
    
          </div> <!-- Keresés ami még nincs -->
             <div class="col-sm">
            <form>
              <div class="form-row align-items-center">
                <div class="col-auto my-1">
                  <label class="mr-sm-2" for="inlineFormCustomSelect">Kategóriák</label>
                  <select class="custom-select mr-sm-2" id="inlineFormCustomSelect">
                    <option selected>válassz kategóriát...</option>
                    <option value="1">Irodalom</option>
                    <option value="2">Tudomás</option>
                    <option value="3">Gyermek</option>
                    <option value="3">vallás</option>
                    <option value="3">Filozófia</option>
                  </select>
                </div>
               
                <div class="col-auto my-1">
                  <button type="submit" class="btn btn-primary">Keresés  </button>
                </div>
              </div>
            </form>   

               <div class="row">
      
      <!-- Új könyv, ez nyitja a modált -->
      <button  
        type="button"
        class="btn btn-primary"
        data-toggle="modal"
        data-target="#addItemModal">Új könyv felvitele </button>
    </div>         
    </div>
          
     </div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="addItemModal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="addItemModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Új könyv felvitele</h5>
            <button
              type="button"
              class="close"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div class="form-row">
                <div class="col-md-4 mb-3">
                  <label for="title">title</label>
                  <input
                    v-model="title"
                    type="text"
                    class="form-control"
                    id="title"
                    value="Egerek és emberek"
                    required
                  />
                </div>
                <div class="col-md-4 mb-3">
                  <label for="author">author</label>
                  <input
                    v-model="author"
                    type="text"
                    class="form-control"
                    id="author"
                    value="Join Steinback"
                    required
                  />
                </div>

                  <div class="col-md-4 mb-3">
                  <label for="category_id">kategória</label>
                  <input
                    v-model.number="category_id"
                    type="number"
                    class="form-control"
                    id="category_id"
                    value=1
                    required
                  />
                </div>
              

                  <div class="col-md-4 mb-3">
                  <label for="piece">Példányszám</label>
                  <input
                    v-model.number="piece"
                    type="number"
                    class="form-control"
                    id="piece"
                    value="7"
                    required
                  />
                </div>
              </div>              
              
            </form>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-dismiss="modal"
            >
              Close
            </button>
            <button @click="addItem()" type="button" class="btn btn-primary">Mentés</button>
          </div>
        </div>
      </div>      
    </div>    
  </div>
</template>

<script>
import TableRow from "@/components/TableRow";
import axios from 'axios';
export default {
  name: "Table",
  data() {
    return {
      tableItems: [],
      title: "",
      author: "",
      category_id: "",     
      piece: 0,
      tableItem: {}
    };
    
  },
  components: {
    TableRow,
  },
  methods: {
    addItem() {
      console.log("additem")
      this.tableItem = {
        title: this.title,
        author: this.author,
        category_id: this.category_id,         
        piece: this.piece
      };
      this.tableItems.push(this.tableItem);
      console.log(this.tableItem)
      axios.post("http://localhost:8000/api/book/", this.tableItem,
      {
          headers: {
            "content-type": "application/json",
            Accept: "application/json"
          }
        })
      .then (res=>{
        console.log(res)
      })
      .catch(err => {
        console.log(err)
      })
    }
  },
  created() {
    axios.get("http://localhost:8000/api/book")
    .then(books => {
      // console.log(books.data)
      this.tableItems=books.data
    })
  },
 


};
</script>
