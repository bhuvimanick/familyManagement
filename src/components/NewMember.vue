<template>
<div>
    <h2>Add New Member</h2>
  

        <form>
        
          <div v-if="errors.length">
            Please correct the following errors
            <ul>
              <li class="redcolor" v-for="error in errors">{{error}}</li>
            </ul>
          </div>
          <div class="form-field">
            <label class="label">Name</label>
            <input type="text" v-model.lazy="famname">
          </div>
          <div class="form-field">
            <label class="meaning">Meaning</label>
            <input type="text" v-model.lazy="famdesc">
          </div>
   

          <div v-if="famname.length">Your name is {{famname}}</div>
          <div v-if="famdesc.length">Your meaning is {{famdesc}}</div>

          <input type="submit" value="ADD" @click.prevent="onSubmitmember"> 
        </form>
       </div>
</template>

<script>
export default {
    name:"NewMember",
    props: ["familyarr"],
    data(){
        return {
            famname:'',
            famdesc:'',
              errors: [],
                    memberlist: [],
        }
    },
    methods: {
    onSubmitmember: function() {
     

      this.errors = [];
      this.memberlist = [];
      if (!this.famname) {
        this.errors.push("Name is required.");
      }
      if (!this.famdesc) {
        this.errors.push("Description is required.");
      }

      this.memberlist.push({
        name: this.famname,
        meaning: this.famdesc
      });
      this.familyarr.push(this.memberlist);
      const family = JSON.stringify(this.familyarr);
      localStorage.setItem("family", family);
      console.log(JSON.stringify(this.memberlist));
    }
  }
    // props:['famname','famdesc']
}
</script>