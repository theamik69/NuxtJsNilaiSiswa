<template>
  <div class="full-table">
  <div class="info">
    <div class="infoSiswa">
      <p>Rata-rata nilai tugas : {{ calculateAverage() }}</p>
      <p>Jumlah siswa          : {{ count }}</p>
    </div>
      <div>
        <input class="cari" type="text" v-model="searchQuery" placeholder="Search"/>
      </div>
    </div>
  <div class="table-container">
    <h2>Daftar Siswa</h2>
    <div class="row">
      <div class="col-md-12">
        <div class="table-wrap">
          <table class="table table-responsive-xl">
            <thead>
              <tr>
                <th>No. Induk Siswa</th>
                <th>Nama Siswa</th>
                <th>Nilai Tugas</th>
                <th> </th>
              </tr>
            </thead>
      <tbody class="isi-tabel">
        <tr class="alert" role="alert" v-for="siswa in filteredSiswaList" :key="siswa.noInduk">
          <td>{{ siswa.noInduk }}</td>
          <td>{{ siswa.nama }}</td>
          <td>{{ siswa.nilai }}</td>
          <td>
            <button @click="hapusSiswa(siswa)" type="button" title="Delete" class="delete">
              <img src="../assets/delete.png" alt="" />
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  </div>
  </div>
  </div>
</div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
export default {
  props: {
    siswaList: {
      type: Array,
      default: () => []
    },
  },
  data() {
      return {
        searchQuery: '' 
      };
    },
  methods: {
    hapusSiswa(siswa) {
      this.$emit('hapus-siswa', siswa);
    },
    calculateAverage() {
      if (this.siswaList.length === 0) {
        return 0;
      }
      const total = this.siswaList.reduce((accumulator, siswa) => {
        return accumulator + siswa.nilai;
      }, 0);
      return (total / this.siswaList.length).toFixed(2);
    }
  },
  computed: {
  filteredSiswaList() {
    if (this.searchQuery) {
      const query = this.searchQuery.toLowerCase();
      return this.siswaList.filter(siswa => {
        return (
          siswa.noInduk.toLowerCase().includes(query) ||
            siswa.nama.toLowerCase().includes(query) ||
            siswa.nilai.toString().includes(query)
        );
      });
    } else {
      return this.siswaList;
    }
  },
  count () {
    return this.siswaList.length;
  }
}
};
</script>

<style scoped>

.info{
  display: flex;
  justify-content: space-between;
  align-items:flex-start;
  padding: 30px 35px 10px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  font-size: 1.5rem;
  font-weight: 500;
  line-height: 1.5rem;
  color: #212529;
  background-color: #F4F4F4;
}

.cari {
  outline: none;
  background-color: #ffffff;
  border-radius: 0.5rem;
  transition: background-color 0.3s ease;
}
.cari:hover {
  background-color: #D5CEA3;
  border-radius: 0.5rem;
}

.full-table {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  text-align: left;
  background-color: #F4F4F4;
  height: 90vh;
}

.table thead th {
    vertical-align: bottom;
    border-bottom: 4px solid #D5CEA3;
  }

  .table thead th {
    padding-bottom: 20px;
    font-size: 1rem;
    font-weight: 500;
    color: rgb(0, 0, 0); }
  .table thead tr {
    background: #fff;
    border-bottom: 4px solid #eceffa; }

  h2 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.table {
  border-radius: 0.25rem;
}
    
th {
  position: sticky;
  top: 0px;
  background-color: #fff;
  color: #1A120B;
}

.table-wrap {
  height: 50vh;
  overflow: auto;
  border-radius: 0.5rem;
}

.table-wrap table {
  margin-bottom: 0; 
  border-radius: 0.25rem;
}

.table-wrap thead th {
  position: sticky;
  top: 0;
  background-color: #F0A500;
  color: #1A120B;
  z-index: 2; 
}

.isi-tabel {
  margin-top: 40px;
}

.alert {
  position: relative;
  padding: 0.75rem 1.25rem;
  border: 1px solid #F0A500;
  border-radius: 0.25rem; 
}

.row {
  margin: 30px;
}

.delete {
  background-color: #fff;
  border: none;
  transition: background-color 0.3s ease;
}

.delete img {
  height: 25px; 
  width: 25px; 
}

.delete:hover {
  background-color: #D5CEA3;
}


</style>
