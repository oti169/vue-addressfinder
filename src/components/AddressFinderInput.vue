<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input type="text" :id="id" :style="'width:' + width + 'px'" />
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
      widget: null
    };
  },

  mounted () {
    bus.$on('afloaded', this.init);
    if (addressFinder.ready) {
      this.init();
    }
  },

  destroyed () {
    bus.$off('afloaded', this.init);
    // Remove widget list element, or it will stick around while new ones are created
    if (this.widget && this.widget.output) {
      this.widget.output.remove()
    }
  },

  methods: {
    init () {
      if (this.ready) {
        return;
      }
      this.ready = true;

      /* eslint-disable no-new */
      this.widget = new window.AddressFinder.Widget(
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
