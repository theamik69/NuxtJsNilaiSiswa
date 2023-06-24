<template>
    <div>
      <FormSiswa @siswa-added="addSiswa" />
      <DaftarSiswa :siswaList="siswaList" @hapus-siswa="hapusSiswa" />
    </div>
  </template>
  
  <script>
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
  
  export default {
    data() {
      return {
        siswaList: [], 
      };
    },
    methods: {
      addSiswa(siswa) {
        this.siswaList.push(siswa);
      },
    hapusSiswa(siswa) {
      const index = this.siswaList.indexOf(siswa);
      if (index > -1) {
        this.siswaList.splice(index, 1);
      }      
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
  }
}
  };
  </script>
  