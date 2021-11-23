<template>
  <div id="app">
    <div class="container d-flex flex-wrap justify-content-center">
      <div class="col-12">
        <h1 class="text-white">Calcs Track</h1>
      </div>
      <div class="card text-white bg-dark mb-3" style="max-width: 30rem;">
        <div class="card-header">
          <h5 class="card-title">{{result}}</h5>
        </div>
        <div class="card-body">
          <div class="row mb-2">
            <div class="col-6">
                <a v-on:click="adddb()" class="btn btn-success btn-block">Add to list</a>
            </div>
            <div class="col-6">
                <a v-on:click="clear()" class="btn btn-danger btn-block">Clear</a>
            </div>
          </div>
          <div class="input-group">
            <input
              type="text"
              v-model="inpt"
              class="form-control text-primary bg-dark"
              aria-label="Text input with segmented dropdown button"
            />
            <div class="input-group-append">
              <button v-on:click="backsp()" class="btn btn-outline-secondary" type="button">
                <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-arrow-left" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" d="M5.854 4.646a.5.5 0 0 1 0 .708L3.207 8l2.647 2.646a.5.5 0 0 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 0 1 .708 0z"/>
  <path fill-rule="evenodd" d="M2.5 8a.5.5 0 0 1 .5-.5h10.5a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
</svg>
              </button>
            </div>
          </div>
          <div class="row py-4">
            <div class="col-4">
              <a v-on:click="add(1)" class="btn btn-primary btn-block mb-2">1</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(2)" class="btn btn-primary btn-block mb-2">2</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(3)" class="btn btn-primary btn-block mb-2">3</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(4)" class="btn btn-primary btn-block mb-2">4</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(5)" class="btn btn-primary btn-block mb-2">5</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(6)" class="btn btn-primary btn-block mb-2">6</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(7)" class="btn btn-primary btn-block mb-2">7</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(8)" class="btn btn-primary btn-block mb-2">8</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(9)" class="btn btn-primary btn-block mb-2">9</a>
            </div>
            <div class="col-4">
              <a v-on:click="add(0)" class="btn btn-primary btn-block mb-2">0</a>
            </div>
            <div class="col-4">
              <a v-on:click="add('+')" class="btn btn-secondary btn-block mb-2">+</a>
            </div>
            <div class="col-4">
              <a v-on:click="add('-')" class="btn btn-secondary btn-block mb-2">-</a>
            </div>
            <div class="col-4">
              <a v-on:click="add('/')" class="btn btn-secondary btn-block mb-2">/</a>
            </div>
            <div class="col-4">
              <a v-on:click="add('*')" class="btn btn-secondary btn-block mb-2">*</a>
            </div>
            <div class="col-4">
              <a v-on:click="add('%')" class="btn btn-secondary btn-block mb-2">%</a>
            </div>
          </div>
        </div>
      </div>
      <div class="col-4">
        <div class="jumbotron bg-dark">
          <div class="mb-2">
            <h2 class="text-white">My list</h2>
          </div>
          <div
            v-for="item in dblist"
            :key="item.key"
            class="btn-group d-flex mb-2"
            role="group"
            aria-label="Basic example"
          >
            <button
              type="button"
              v-on:click="doCopy(item)"
              style="max-width: 40px"
              class="btn btn-secondary flex-fill"
              data-container="body"
              data-toggle="popover"
              data-placement="left"
              data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus."
            >
              <svg
                width="1em"
                height="1em"
                viewBox="0 0 16 16"
                class="bi bi-clipboard"
                fill="currentColor"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill-rule="evenodd"
                  d="M4 1.5H3a2 2 0 0 0-2 2V14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V3.5a2 2 0 0 0-2-2h-1v1h1a1 1 0 0 1 1 1V14a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V3.5a1 1 0 0 1 1-1h1v-1z"
                />
                <path
                  fill-rule="evenodd"
                  d="M9.5 1h-3a.5.5 0 0 0-.5.5v1a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-1a.5.5 0 0 0-.5-.5zm-3-1A1.5 1.5 0 0 0 5 1.5v1A1.5 1.5 0 0 0 6.5 4h3A1.5 1.5 0 0 0 11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3z"
                />
              </svg>
            </button>
            <button type="button" class="btn btn-secondary flex-fill">
              <i></i>
              {{item}}
            </button>
            <button
              type="button"
              v-on:click="deldb(item)"
              style="max-width: 40px"
              class="btn btn-danger"
            >
              <svg
                width="1em"
                height="1em"
                viewBox="0 0 16 16"
                class="bi bi-trash"
                fill="currentColor"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"
                />
                <path
                  fill-rule="evenodd"
                  d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4L4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"
                />
              </svg>
            </button>
          </div>
          <div class="text-white mt-2">Total: <h3><span class="badge badge-secondary">{{totaldb}}</span></h3></div>
          <div>
            <a v-on:click="clearlist()" class="btn btn-danger btn-block">Clear List</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      inpt: "0",
      dbs: [],
    };
  },
  computed: {
    exp() {
      var allowed = /[^\d*/+,.(%√)-]/g;
      var pow = /(\d+)\*\*(\d+)/g;
      return this.inpt.replace(allowed, " ").replace(pow, "Math.pow($1, $2)");
    },
    result() {
      if (this.inpt) {
        try {
          return eval(this.exp);
        } catch (e) {
          return e.message;
        }
      } else return "0";
    },
    dblist() {
      return this.dbs;
    },
    totaldb() {
      return this.dbs.reduce(function (a, b) {
        return a + b;
      }, 0);
    },
  },
  methods: {
    add(n) {
      if (this.inpt != "0") {
        console.log(n);
        n = n.toString();
        this.inpt += n;
      } else {
        this.inpt = n;
      }
    },
    backsp() {
      this.inpt = this.inpt.substring(0, this.inpt.length - 1);
    },
    adddb() {
      this.dbs.push(this.result);
    },
    deldb(del) {
      this.dbs.splice(this.dbs.indexOf(del), 1);
    },
    clear(){
        this.inpt = 0;
    },
    clearlist(){
        this.dbs = []
    },
    doCopy: function (item) {
      this.$copyText(item).then(
        function () {
          console.log("copied");
        },
        function () {
          console.log("can not copy");
        }
      );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
  min-height: 100vh;
  background-color: #40484f;
}
input[type="text"] {
  border: 1px solid #6c757d;
}
</style>
