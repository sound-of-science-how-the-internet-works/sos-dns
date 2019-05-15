<template lang="pug">
feathers-vuex-find(service="states", :query="{}", watch="query", :edit-scope="prepareStates")
  section(slot-scope="{ dns }")
    .octet-group
      .octet(v-for="state of dns", :key="dns.qid") {{ state }}
</template>

<script>
export default {
  name: 'Index',
  methods: {
    prepareStates(scope) {
      if (scope.items.length > 0) {
        scope.dns = scope.items.filter(obj => {
          return obj.panel === 'dns'
        })[0].data.ip
      }
    }
  }
}
</script>

<style lang="postCss">
@font-face {
  font-family: digital;
  //src: url(/fonts/Digital_tech.otf);
  src: url(/fonts/Prudencia%20Digital.ttf);
  //src: url(/fonts/digital-7.ttf);
  //src: url(/fonts/modern_dot_digital-7.ttf);
}

body {
  background-color: white;
  color: black;
  font-family: digital;
}

.octet-group {
  @apply .flex;
}
.octet {
  font-size: 15vw;
  @apply .flex-1 .text-center .p-5;
}
/*.octet-1 {
  transform: rotate(20deg);
}
.octet-2 {
  transform: rotate(-15deg);
}
.octet-3 {
  transform: rotate(10deg);
}
.octet-4 {
  transform: rotate(-10deg);
}*/
</style>
