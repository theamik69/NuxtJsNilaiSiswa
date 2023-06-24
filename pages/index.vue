<template>
  <div class="content">
    <section class="hero py-4">
      <form @submit.prevent="submitUser">
      <div class="userInput text-center">
        <h1 class="title mb-4">Siapa nama mu ?</h1>
        <input class="textField" type="text" id="userName" v-model="user.Name">
      </div>
      <div class="text-center">
        <button class="btn btn-primary" @click="submitForm" >Masuk</button>
      </div>
    </form>
    </section>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'


export default {
  data() {
    return {
      user: {
        Name: ''
      }
    };
  },
  methods: {
    submitUser() {
      if (this.user.Name.trim() === '') {
        alert('Silakan isi nama Anda sebelum melanjutkan');
      } else {
        console.log('Nama pengguna:', this.user.Name);
        this.$emit('userName-submitted', this.user.Name);
        this.$router.push('/app');
      }
    }
  }
};
</script>

<style>
body {
  margin: 0; 
  padding: 0;
  background: #eee455;
}


.content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  background: #F0A500;
  width: 100%;
  height: 100vh;
  margin: auto;
}

.hero {
  width: 100%;
  height: 100vh;
}

.title {
  margin-top: 5rem;
}

.userInput {
  margin-bottom: 4rem;
}

.textField {
  line-height: 3rem;
  font-size: 1.75rem;
  font-weight: 500;
  text-align: center;
  border-radius: 1rem;
  outline: none;
  border: none;
}

.textField:hover {
  background-color: #c7e3eb;
}

.btn {
  line-height: 2rem;
}

</style>
