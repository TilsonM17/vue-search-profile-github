<template>
  <nav class="navbar navbar-expand-md navbar-dark bg-dark shadow-sm">
      <div class="container">
        <a class="navbar-brand" href=""> GithubProfile </a>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <!-- Right Side Of Navbar -->
          <ul class="navbar-nav ms-auto">
            <button v-if="modo_atual"
              class="btn btn-outline-primary"
              type="button"
              @click="Noturno()"
            >
              Dark
            </button>

            <button v-else
              class="btn btn-outline-primary"
              type="button"
              @click="Diurno()"
            >
              Ligth
            </button>
          </ul>
        </div>
      </div>
    </nav>
</template>

<script>
export default {
    name: 'nav-bar',
    data(){
        return{
           ObjectColor:"",
           color_d: '#ffffff',
           color_n: '#000000',
           modo_atual:true,
        }
    },
    mounted(){
            this.ObjectColor = {
        "background-color": localStorage.getItem('background-color'),
        color: localStorage.getItem('color')
     }
    },
    methods:{
     Noturno: function () {
      this.ObjectColor = {
        "background-color": this.color_n,
        color: this.color_d,
      };
      localStorage.setItem('background-color',this.color_n)
      localStorage.setItem('color',this.color_d)

      this.modo_atual = false;
    },
    Diurno: function () {
      this.ObjectColor = {
        "background-color": this.color_d,
        color: this.color_n,
      };
      localStorage.setItem('background-color',this.color_d)
      localStorage.setItem('color',this.color_n)

      this.modo_atual = true;
    },
    }
     
}
</script>

<style>

</style>