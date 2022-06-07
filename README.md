# Vue 3 Component for Address Completion

This is a [Vue 3 Component](/src) for address autocompletion. It integrates with 
[Mapbox Geocoding API](https://docs.mapbox.com/api/search/geocoding/) and [Bootstrap 5](https://getbootstrap.com).

A current build of the component library can be found in the *dist* directory.
A current build of the example app can be found in the *docs* directory so it can be served on GitHub Pages.

## Installation
```bash
npm install @samhess/vue-address-input```

## Usage 
```html
<template>
  <AddressInput @addressSelect="getAddress" :mapboxOptions="mapboxOptions"></AddressInput>
</template>

<script setup>
  import { reactive } from 'vue'
  // import AddressInput from './components/AddressInput.vue'
  // import AddressInput from '../lib/AddressInput.js'
  import AddressInput from '@samhess/vue-address-input'
  const editedItem = reactive({})
  // mapbox options as per https://docs.mapbox.com/api/search/geocoding
  const mapboxOptions = {
    access_token : 'YOUR_TOKEN',
    limit : 10,
    language: 'de'
  }
  function getAddress(address) {
    Object.assign(editedItem,address)
  }
</script>
```

## Demo
[Demo](https://samhess.github.io/vue3-address-input/index.html) is hosted on GitHub Pages ([docs](/docs) directory)

## Properties

| Property                   | Type   | Description                        | Required | Default |
| :------:                   | :---:  | :---------:                        | :------: | :-----: |
| mapboxOptions              | Object | Mapbox options as indicated below  | Yes      | []      |
| mapboxOptions.access_token | String | Mapbox access token                | Yes      | null    |
| mapboxOptions.limit        | String | Limit of suggestions               | No       | 10      |
| mapboxOptions.proximity    | String |                                    | No       |'ip'     |
| mapboxOptions.autocomplete | Boolean|                                    | No       | true    |
| mapboxOptions.fuzzyMatch   | Boolean|                                    | No       | true    |
| mapboxOptions.country      | String |                                    | No       | null    |
| mapboxOptions.language     | String |                                    | No       | 'en'    |

Please refer to [Mapbox Geocoding API documentation](https://docs.mapbox.com/api/search/geocoding) for further information

## Events

| Event | Description |
| :---: | :---------: |
| **@addressSelect** | Triggered when user selects address. Returns object with selected address containing street, postcode, city state and country |