# addressfinder

AddressFinder is a widget you can use to look up addresses in Australia and New Zealand. See https://addressfinder.com.au for more information.

This code is a wrapper around their widget (see https://addressfinder.com.au/docs/getting_started/).

I built this with the following commands:

``` bash
vue init webpack addressfinder
cd addressfinder/
npm install
npm run dev
```
... and chose the Airbnb eslint scheme.

I added the following files to the project:
* src/components/AddressFinderInput.vue
* src/utils/addressfinder.js
* src/utils/eventbus.js

I edited HelloWorld.vue, replacing most of the template code with this:
``` html
<address-finder-input
  id="my-address-input"
  label="Start typing an address"
  width="300"
></address-finder-input>
```
and changed the script so that it looks like this:
``` javascript
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
```

Finally, src/main.js now contains the following lines:

``` javascript
import addressfinder from './utils/addressfinder';
addressfinder.initialise();
```

I don't know if this is the best way to do these things, so please let me know if you have a better idea.