<template>
  <div class="home">
    <h2>home</h2>
    <div class="list-contacts">
      <button type="button" class="btn"  @click="openModal('dv-modal')">DELETE</button>
      <button type="button" class="btn2">CHANGE</button>
      <img class="imgServer" src="https://colegiocognos.com.br/wp-content/uploads/2020/08/essa-pessoa-nao-existe.jpeg">
    </div>
    <div class="list-contacts">
      <button type="button" class="btn" @click="openModal('dv-modal')">DELETE</button>
      <button type="button" class="btn2">CHANGE</button>
      <img class="imgServer" src="https://engenharia360.com/wp-content/uploads/2019/05/esta-pessoa-nao-existe-engenharia-360-2.png">
    </div>
    <div id="dv-modal" class="modal">
      <div id="dv2-modal">
        <label>Do you really want to delete this contact?</label>
        <button type="button" id="deleteContact" @click="closeModal('dv-modal')">CONFIRM</button>
        <button type="button" id="btnCancel" @click="closeModal('dv-modal')">CANCEL</button>
      </div>
    </div>
  </div>
</template>


        //  **STATIC DATA BECAUSE I CANNOT EXTRACT FROM DB.JSON***


<script>
    
    export default {
      
      data() {
        return {
        name_contact: null,
        openModal,
        closeModal
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

 function openModal(mn) {
    let modal = document.getElementById(mn);

    if (typeof modal == 'undefined' || modal === null)
    return;
    modal.style.display = 'Block';
    document.body.style.overflow = 'hidden';
  }

  function closeModal(mn) {
    let modal = document.getElementById(mn);

    if (typeof modal == 'undefined' || modal === null)
    return;
    modal.style.display = 'none';
    document.body.style.overflow = 'auto';
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
   color: white;
   background-color: red;
   font-weight: bold;
   margin-left: 1400px;
   margin-top: 67px;
   height: 180px;
   width: 150px;
   border-radius: 40px;
 }

 .btn:hover {
   background-color: rgb(228, 177, 177);
   height: 190px;
   width: 160px;
 }

 .btn2 {
   color: white;
   background-color: rgb(7, 76, 133);
   font-weight: bold;
   margin-left: 1600px;
   margin-top: -73px;
   height: 180px;
   width: 150px;
   border-radius: 40px;
 }

 .btn2:hover {
   background-color: rgb(113, 143, 241);
   height: 190px;
   width: 160px;
 }

 #deleteContact {
   background-color: red;
   color: white;
   font-weight: bold;
   height: 100px;
   width: 150px;
   margin-top: 120px;
   margin-left: 100px;
   padding: 40px;
 }

 #deleteContact:hover {
   background-color: rgb(241, 141, 141);
 }

 #btnCancel {
   background-color: rgb(37, 85, 30);
   color: white;
   font-weight: bold;
   height: 100px;
   width: 150px;
   margin-top: 120px;
   margin-left: 120px;
   padding: 40px;
 }

 #btnCancel:hover {
   background-color: rgb(148, 175, 143);
 }


 .imgServer {
   height: 300px;
   width: 300px;
   border-radius: 200px;
   margin-top: -460px;
   margin-left: 80px;

 }

 .modal {
   background-color: rgb(0, 0, 0, .8);
   position: fixed;
   top: 0;
   left: 0;
   width: 100vw;
   height: 100vh;
   display: none;
 }

 #dv2-modal {
   width: 600px;
   height: 300px;
   border-radius: 45px;
   background-color: #fff;
   align-items: center;
   justify-content: center;
   margin-left: 690px;
   margin-top: 250px;
 }
 
 label {
   padding:30px;
   font-size: 30px;
 }
</style>
