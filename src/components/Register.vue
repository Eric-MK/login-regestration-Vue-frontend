<!-- eslint-disable vue/multi-word-component-names -->
<template>

    <div class="card" align="left">
            <div class="card-header">Register Form</div>
            <div class="card-body"> 
            <!-- //The v-model directive is used to bind the form input fields to the student
data object. When the user enters data into the input fields, the student data object is updated.
              -->   
              <form  @submit.prevent="saveData"><!-- The @submit.prevent directive is used to prevent the default form submission behavior and call the saveData method -->
                
                <label>First Name</label>
                <input type="text" v-model="student.name" name="name" id="name" class ="form-control"/> 
    
          
                <label>Email</label>
                <input type="email" v-model="student.email" name="email" id="email" class ="form-control"/>
    
                <label>Password</label>
                <input type="password" v-model="student.password" name="password" id="password" class ="form-control"/> 
    
    
                <input type="submit" value="Save" class="btn btn-success"> 
    
    
                </form>
            </div>
        </div>
    </template>
       
       <script>
          // import Vue from 'vue';
           import axios from 'axios';
           //Vue.use(axios);

         export default {
           // eslint-disable-next-line vue/multi-word-component-names
           name: 'Register',
           data () {
             return {
               result: {},
               student:{
                          name: '',
                          email: '',
                          password: ''
               }
             }
           },
           created() { 
           },
           mounted() {
                 console.log("mounted() called.......");
             },
           methods: {
                  saveData()
                  {
                   axios.post("http://127.0.0.1:8000/api/register", this.student)/* The axios.post method takes two arguments: the URL of the server endpoint and the data to be sent to the server. */
                   .then(
                     ({data})=>{
                      console.log(data);
                       try /*  If the server responds with an error status code, the catch method is called,
and an alert is displayed to indicate that the data could not be saved. */
                         {
                            alert("saveddddd");
                            
                          } 
                      catch(err) 
                          {
                            alert("failed");
                          }    
                     }
                   )
                  }
             }
         }
         </script>