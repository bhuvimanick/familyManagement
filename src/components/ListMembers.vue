<template>
  <div>
    <div v-if="familyarr.length">
      <h3 class="colorblue">List of Members</h3>
      <div v-for="memb in familyarr">
        <p>
          Name
          {{Object.values(memb)[0].name}}
          <b>Meaning is</b>
          {{Object.values(memb)[0].meaning}}
        </p>
      </div>
    </div>
    <div v-else>No list of members</div>
  </div>
</template>
<script>
export default {
  name: "ListMembers",
  props: ["familyarr"]
};
</script>
<style>

.colorblue{
  color: blue;
}
</style>
