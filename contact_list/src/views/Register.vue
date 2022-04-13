<template>
    <div class="register">
        <h1>REGISTER CONTACT</h1>
        <div>
            <form id="formCad" @submit="createContact">
                <input type="text" id="name" name="name_contact" v-model="name" placeholder="Type it a name here"><br><br>
                <input type="text" id="contact" name="contact"  v-model="contact" placeholder="Please, type it a number"><br><br>
                <input type="email" id="email" name="email_contact" v-model="email" placeholder="Please, type it a valid email"><br><br>
                <input type="file" id="file" accept="image/*"/><br><br>
                <input type="submit" class="submit-btn" value="Make Contact">
            </form>
        </div>
    </div>
</template>

<script>
   export default {
     register() {
    return {
        id_contact: null,
        name_contact: null,
        contact: null,
        email_contact: null,
        imgLink_contact: null
        }
      },
      methods: {
        async createContact(e) {
          if (this.contact.length > 9 || this.contact.length < 9) {
            alert("Please, type it a number valid");
            disable("submit-btn");
          }else if(this.file == '') {
            alert("Please, select a file");
          }else{

          e.preventDefault();
          
          const data = {
            name_contact : this.name,
            contact : this.contact,
            email_contact : this.email,
            imgLink_contact : this.imgLink,
          }
          const dataJson = JSON.stringify(data);
          
           const req = await fetch("http://localhost:3000/contacts", {
             method: "POST",
             headers: {"Content-Type": "application/json"},
             body: dataJson
           });

          const res = await req.json();
          console.log(dataJson)

        }
      }
    }
   }
</script>

<style>
   .register {
     padding: 280px;
     margin-left: 542px;
     background-color: #fff;
     height: 100px;
     width: 100px;
     border-radius: 400px;
     font-size: 25px;
   }

   #formCad {
    margin-left: -100px;
   }

   h1 {
     margin-top: -175px;
     margin-left: -43px;
     font-family: arial;
   }

   .submit-btn {
   background-color: rgb(37, 85, 30);
   color: white;
   font-weight: bold;
   height: 100px;
   width: 150px;
   }
</style>

