<template>
<div>
<h2>Add Stories</h2>
<form v-on:submit.prevent="submitstory">
  <div class="form-field">
            <label class="label">Stories Name</label>
            <input type="text" v-model="storyname">
          </div>
            <div class="form-field">
            <label class="label">Stories Description</label>
            <textarea  v-model="storydesc"></textarea>
          </div>
          <input type="submit" value="Submit"/>

    </form>


    </div>
</template>
<script>
import axios from "axios";
export default {
    name:"AddStories",
    data(){
        return {
            storyname :"",
            storydesc:""
        }

    },
    methods:{
    
       submitstory:function(){
          let data1={
           name:this.storyname,
           description:this.storydesc
         }
          console.log(data1); 
          axios.post('http://localhost:4000/store',data1)
       } 
    }
}

</script>