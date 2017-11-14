<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <address-finder-input
      id="my-address-input"
      label="Start typing an address"
      width="300"
    ></address-finder-input>
  </div>
</template>

<script>
import AddressFinderInput from './AddressFinderInput';

export default {
  name: 'HelloWorld',
  components: {
    AddressFinderInput,
  },
  data() {
    return {
      msg: 'AddressFinder / Vue.js demo',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
