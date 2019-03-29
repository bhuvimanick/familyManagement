<template>
  <div class="hello">
    <h1>{{ welcomemsg }}</h1>
<NavItem></NavItem>
{{datainfo}}
    <div>
      <ListMembers :familyarr="familyarr"></ListMembers>

      <NewMember :familyarr="familyarr"></NewMember>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ListMembers from "./ListMembers.vue";
import NewMember from "./NewMember.vue";
import NavItem from "./NavItem.vue";
export default {
  name: "HelloWorld",
  components: {
    ListMembers,
    NewMember,
    NavItem
  },
  data() {
    return {
      welcomemsg: "Welcome to Your Vue.js MyProject",
      // famname: "",
      // famdesc: "",

      familyarr: [],
      datainfo:null
    };
  },
  mounted() {
    if (localStorage.getItem("family")) {
      try {
        this.familyarr = JSON.parse(localStorage.getItem("family"));
      } catch (e) {
        localStorage.removeItem("family");
      }
    }
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.datainfo = response))
  }
  // methods: {
  //   onSubmitmember: function() {
  //     // return this.welcomemsg

  //     this.errors = [];
  //     this.memberlist = [];
  //     if (!this.famname) {
  //       this.errors.push("Name is required.");
  //     }
  //     if (!this.famdesc) {
  //       this.errors.push("Description is required.");
  //     }

  //     this.memberlist.push({
  //       name: this.famname,
  //       meaning: this.famdesc
  //     });
  //     this.familyarr.push(this.memberlist);
  //     const family = JSON.stringify(this.familyarr);
  //     localStorage.setItem("family", family);
  //     console.log(JSON.stringify(this.memberlist));
  //   }
  // }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-field {
  margin-bottom: 2em;
}
.redcolor {
  color: red;
}
</style>
