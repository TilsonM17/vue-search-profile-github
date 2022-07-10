<template>
  <div>
    <div class="col-md-8 mt-4 offset-md-3">
      <p class="h3 mt-5 text-center">Pesquise um usuario do GitHub.</p>

      <div class="my-3">
        <input
          type="text"
          placeholder="Digite o nome do Usuario no GitHub"
          name="user"
          class="form-control"
          id=""
          v-model="nome_user"
        />
      </div>
      <div class="my-3">
        <button class="btn btn-outline-primary" @click="GetUserApi()">
          Pesquisar
        </button>
      </div>
    </div>
    <hr />

    <div class="row">
      <div class="col-md-6">
        <img class="img img-fluid" :src="img" />
      </div>

      <div class="col-md-6">
        <p class="h5 text-center mb-3">
          <strong>
            <a :href="link_profile">{{ user_name }}</a>
          </strong>
        </p>
        <p class="h5 text-center">
          <strong>{{ seguidores }}</strong>
        </p>
        <p class="h5 text-center">
          <strong>{{ repo }} </strong>
        </p>

        <div class="text-center my-3">
          <li v-for="repo in repositorios" :key="repo.id">
            <a href="#">{{ repo.name }}</a>
          </li>
        </div>
      </div>
      <div class="fixed-bottom"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "FormRequest",
  data() {
    return {
      nome_user: "",
      repositorios: [],
      url_repo: "",
      user: [],
      link_profile: "",
      user_name: "",
      img: "",
      seguidores: "",
      repo: "",
    };
  },
  methods: {
    GetUserApi() {
      //Saber se o User Digitou Algo na Tela
      if (this.nome_user.length == 0) {
        alert("Digite um nome");
        return;
      }

      // Make a request for a user with a given ID

      axios
        .get(`https://api.github.com/users/${this.nome_user}`)
        .then((response) => {
          this.user = response.data;
          //Atribui os dadõs nos respectivos lugares
          this.user_name = this.user.login;
          this.img = this.user.avatar_url;
          this.link_profile = this.user.html_url;
          this.seguidores = this.user.followers + " Seguidores";
          this.repo = this.user.public_repos + " Repositorios";

          this.GetRepositores(this.user.repos_url);
          //console.log(this.user);
        })
        .catch(function () {
          alert("Este utlizador não existe!");
        })
        .then(function () {});
    },
    GetRepositores(url) {
      axios
        .get(url + "?per_page=4")
        .then((response) => {
          this.repositorios = response.data;

          console.log(this.repositorios);
        })
        .catch(function () {})
        .then(function () {});
    },
    Tema() {
      localStorage.setItem("tema", 0);
    },
  },
};
</script>

<style>
</style>