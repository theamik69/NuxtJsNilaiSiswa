  <template>
    <div class="form">
      <div class="form-container">
        <h2 class="mb-4 mt-4 text-center">Form Input Siswa</h2>
      <form class="formField" @submit.prevent="submitForm">
        <div class="form-group">
          <input class="form-input" type="text" id="noInduk" placeholder="No. Induk" v-model="siswa.noInduk" required>
        </div>
        <div class="form-group">
          <input class="form-input" type="text" id="nama" placeholder="Nama Siswa" v-model="siswa.nama" required>
        </div>
        <div class="form-group">
          <input class="form-input" type="number" id="nilai" placeholder="Nilai Tugas" v-model="siswa.nilai" required>
        </div>
        <button class="submit" type="submit">Submit</button>
      </form>
    </div>
    </div>
  </template>

  <script>
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
  export default {
    data() {
      return {
        siswa: {
          noInduk: '',
          nama: '',
          nilai: null
        }
      };
    },
    methods: {
      submitForm() {
        this.$emit('siswa-added', this.siswa);
        this.siswa = {
          noInduk: '',
          nama: '',
          nilai: null
        };
      }
    }
  };
  </script>

  <style scoped>
  .form-group {
    margin-bottom: 15px;
  }

  .form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    background: #e48810;
    width: 100%;
    height: 70vh;
    margin-right: auto;
    margin-left: auto;
  }

  .hiUser {
    width: 20%;
    height: 59vh;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
  }
  .form-container {
    display: flex;
    width: 80%;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 2.4rem;
    margin-left: 8rem;
    background: #000000;
    border: none;
    border-radius: 4rem;
    height: 59vh;
  }

  h2 {
    font-family: sans-serif;
    font-weight: 900;
    color: rgb(255, 254, 254);
  }

  .formField {
    background: #F0A500;
    display: block;
    width: 50%;
    border: none;
    border-radius: 3rem;
    padding-left: 30px;
    padding-right: 30px;
    padding-top: 30px; 
    padding-bottom: 30px;
  }
  .form-input {
    display: block;
    width: 100%;
    height: calc(1.5em + 0.75rem + 2px);
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    background-color: form-input#E5E5CB;
    background-clip: padding-box;
    border-radius: 0.25rem;
    border: none;
    padding-left: 20px;
    padding-right: 20px; 
    transition: background-color 0.3s ease;
  }
  .form-input:hover {
    background-color: #D5CEA3;
    color: #000000;
  }

  .submit {
    display: block;
    width: 100%;
    padding: 0.375rem 0.75rem;
    font-size: 1.5rem;
    font-weight: 500;
    line-height: 1.5;
    color: #01080f;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    border-radius: 0.25rem;
    transition: background-color 0.35s ease;
  }
  .submit:hover {
    background-color: #000000;
    color: #fff;
  }

  /* Media Queries */
  @media (max-width: 768px) {
    .form-container {
      width: 80%;
    }

    .formField {
      width: 70%;
    }
  }
  </style>
