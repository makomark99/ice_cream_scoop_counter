<template>
  <div class="container mx-auto row">
    <h2 class="text-center col-12 mb-5">Gombócok számolása</h2>

    <div class="mb-3 row">
        <div class="d-grid d-md-flex gap-2 col-12">
        <div class="input-group h-75 w-75 mb-3">
          <span
            class="input-group-text bg-primary text-white"
            
            >1 gombóc</span
          >
          <input type="number" :value="price" @change="onInput" class="form-control"  />
          <span
            class="input-group-text bg-primary text-white"
            
            >Ft</span>
          
        </div>
         </div>
      <div class="d-grid d-md-flex gap-2 col-12">
        <button
          @click="inc(1)"
          class="btn btn-outline-warning btn-lg w-75 mb-3"
        >
          Vanília {{ vaniliaDB }}db
        </button>
        <button @click="del(1)" class="btn btn-outline-warning btn-lg mb-3">
          Törlés
        </button>
      </div>
      <div class="d-grid d-md-flex gap-2 col-12">
        <button
          @click="inc(2)"
          class="btn btn-outline-secondary btn-lg w-75 mb-3"
        >
          Csoki {{ csokiDB }}db
        </button>
        <button @click="del(2)" class="btn btn-outline-secondary btn-lg mb-3">
          Törlés
        </button>
      </div>
      <div class="d-grid d-md-flex gap-2 col-12">
        <button @click="inc(3)" class="btn btn-outline-info btn-lg w-75 mb-3">
          Sztracsatella {{ sztracsaDB }}db
        </button>
        <button @click="del(3)" class="btn btn-outline-info btn-lg mb-3">
          Törlés
        </button>
      </div>
      <div class="d-grid d-md-flex gap-2 col-12 mb-3">
        <button @click="inc(4)" class="btn btn-outline-danger btn-lg w-75 mb-3">
          Édestölcsér {{ etolcserDB }}db
        </button>
        <button @click="del(4)" class="btn btn-outline-danger btn-lg mb-3">
          Törlés
        </button>
      </div>
      <div class="d-grid d-md-flex gap-2 col-12">
        <div class="input-group h-75 w-75">
          <span
            class="input-group-text bg-primary text-white"
            
            >Végösszeg</span
          >
          <input type="number" :value="sum" class="form-control" disabled />
          <span
            class="input-group-text bg-primary text-white"
            
            >Ft</span>
          
        </div>
        <button @click="defaultVal" class=" btn btn-outline-primary mb-3">
            Alaphelyzet
          </button>
      </div>
    </div>
  </div>
</template>

<script >
export default {
  data() {
    return {
      vaniliaDB: 0,
      csokiDB: 0,
      sztracsaDB: 0,
      etolcserDB: 0,
      sum: 0,
      price:450,
    };
  },

  methods: {
    onInput(e){
        this.price=Number(e.target.value);
    },
    inc(num) {
      if (num == 1) this.vaniliaDB++;
      else if (num == 2) this.csokiDB++;
      else if (num == 3) this.sztracsaDB++;
      else if (num == 4) this.etolcserDB++;
    },
    del(num) {
      if (this.vaniliaDB >= 1) {
        if (num == 1) this.vaniliaDB--;
      }
      if (this.csokiDB >= 1) {
        if (num == 2) this.csokiDB--;
      }
      if (this.sztracsaDB >= 1) {
        if (num == 3) this.sztracsaDB--;
      }
      if (this.etolcserDB >= 1) {
        if (num == 4) this.etolcserDB--;
      }
    },
    defaultVal(){
        this.vaniliaDB=0;
        this.csokiDB=0;
        this.sztracsaDB=0;
        this.etolcserDB=0;
    },
    summarize(){

            this.sum =
        this.vaniliaDB * this.price +
        this.csokiDB * this.price +
        this.sztracsaDB * this.price +
        this.etolcserDB * 100
    }
  },
  watch: {
    vaniliaDB: function () {
      return this.summarize();
    },
    csokiDB: function () {
      return this.summarize();
    },
    sztracsaDB: function () {
      return this.summarize();
    },
    etolcserDB: function () {
      return this.summarize();
    },
  },
};
</script>

<style>
button {
  font-size: 2em !important;
}
input {
  font-size: 1.8em !important;
}
span {
  font-size: 1.8em !important;
}
</style>