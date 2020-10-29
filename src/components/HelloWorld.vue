<template>
  <form @submit.prevent="submitForm" autocomplete="off">
    <input type="text" Placeholder="Name" v-model="form.name" required><br>
    <p v-if="!nameIsValid">*name is required</p>
    <input type="text" Placeholder="Age" v-model.number="form.age" required><br>
    <p v-if="!ageIsValid">*age is required</p>
    <input type="text" Placeholder="Phone number" v-model="form.phonenumber" required><br>
    <form>
    <input type="radio" name="gender" value="male">
    <label for="male">Male</label>
    <input type="radio" name="gender" value="female">
    <label for="male">Female</label>
    </form><br>
    <label>Holiday</label><br>
    <select>
    <option v-for="holiday in holidays" :key="holiday">{{ holiday }}</option>
    </select><br>
    <div id="butter">
    <button>Submit</button>
    <button @click="resetInput">Cancel</button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      form:{
      error:[],
      name:null,
      age:null,
      phonenumber:null,
      },
      holidays: ['Christmas','New year','Haloween','Thanksgiving']
    }
  },
  computed:{
    nameIsValid(){
      return !!this.form.name
    },
    ageIsValid(){
      return typeof this.form.age==='number' && this.form.age>12 && this.form.age<80
    },
    formIsValid(){
      return this.nameIsValid && this.ageIsValid
    }
  },
  methods:{
    submitForm(){
      if(this.formIsValid){
        alert('form submitted successfully',this.form)
      }
      else{
      alert('Invalid form')
    }
    },
    resetInput(){
     this.form.name="",
     this.form.age="",
     this.form.phonenumber=""
    }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
  margin:0;
  padding:0;
}
  input[type="text"]{
    border:3px solid black;
    border-radius:20px;
    width:15%;
    height:5%;
    padding:5px;
    margin:10px;
  }
  label{
    color:black;
    justify-content:center;
    display:inline-content;
  }
  select{
    border:3px solid black;
    border-radius:20px;
    width:15%;
    height:5%;
    padding:5px;
    margin:10px;
  }
  button{
    padding:5px;
    margin:10px;
    width:15%;
    height:5%;
    border-radius:5px;
    background:#00ff00;
    border:3px solid black;
    box-shadow:0 1px 0 1px;
  }
  p{
    color:red;
  }
</style>
