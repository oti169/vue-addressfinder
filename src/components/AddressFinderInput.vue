<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input type="text" :id="id" :style="'width:' + width + 'px'"></input>
  </div>
</template>

<script>
import addressFinder from '../utils/addressfinder';
import bus from '../utils/eventbus';

export default {
  name: 'AddressFinderInput',

  props: [
    'id',
    'label',
    'width',
  ],

  data() {
    return {
      ready: false,
    };
  },

  mounted() {
    bus.$on('afloaded', this.init);
    if (addressFinder.ready) {
      this.init();
    }
  },

  methods: {
    init() {
      if (this.ready) {
        return;
      }
      this.ready = true;

      /* eslint-disable no-new */
      new window.AddressFinder.Widget(
        document.getElementById(this.id),
        'ADDRESSFINDER_DEMO_KEY',
        'AU',
        {});
    },
  },
};
</script>

<style>

</style>
