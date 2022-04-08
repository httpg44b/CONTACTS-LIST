<template>
  <div class="home">
    <h2>home</h2>
    <div class="list-contacts">
      <button type="button" class="btn">EXCLUIR</button>
      <button type="button" class="btn2">ALTERAR</button>
      <img class="imgServer" src="https://colegiocognos.com.br/wp-content/uploads/2020/08/essa-pessoa-nao-existe.jpeg">
    </div>
    <div class="list-contacts">
      <button type="button" class="btn">EXCLUIR</button>
      <button type="button" class="btn2">ALTERAR</button>
      <img class="imgServer" src="https://engenharia360.com/wp-content/uploads/2019/05/esta-pessoa-nao-existe-engenharia-360-2.png">
    </div>
  </div>
</template>

        //  **STATIC DATA BECAUSE I CANNOT EXTRACT FROM DB.JSON***

<script>
    export default {
      data() {
        return {
        name_contact: null,
        }
      },
      methods: {
        async getUsers() {
          const req = await fetch('http://localhost:3000/contacts');
          const data = await req.json();


          this.name = data.name_contact;

          
          console.log(data.name_contact)
        }
      },
      mounted() {
        this.getUsers()
      }
    }

</script>

<style>
 body {
   background-image: linear-gradient( to right, black, rgba(8, 9, 95, 0.74), rgba(16, 101, 122, 0.603), black );
 }

 .list-contacts {
   background-color: white;
   height: 400px;
   width: 1910px;
   margin-top:240px;
   border-radius: 300px;
 }

 .btn {
   font-style: white;
   background-color: red;
   font-weight: bold;
   margin-left: 1400px;
   margin-top: 67px;
   height: 180px;
   width: 150px;
 }

 .btn2 {
   font-style: white;
   background-color: rgb(7, 76, 133);
   font-weight: bold;
   margin-left: 1600px;
   margin-top: -73px;
   height: 180px;
   width: 150px;
 }

 .imgServer {
   height: 300px;
   width: 300px;
   border-radius: 200px;
   margin-top: -460px;
   margin-left: 80px;

 }
</style>
