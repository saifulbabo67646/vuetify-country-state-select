<template>
    <v-autocomplete
      :items="countries"
      item-text="countryName"
      item-value="text"
      :value="value"
      v-model="country"
      :outlined="outlined"
      :filled="filled"
      :flat="flat"
      :label="label"
      :country="country"
      :rules="rules"
      @input="selectCountry()"
      return-object
    ></v-autocomplete>
</template>


<script>
import { VAutocomplete } from "vuetify/lib";
import countries from "@/data.js";
// import { EventBus } from "../main";
import { EventBus } from "@/event";

export default {
  name: "VCountrySelect",
  extends: VAutocomplete,
  props: {
    countriess: {
      type: [Array],
    },
    backgroundColor: {
      type: String,
    },
    clearable: {
      type: Boolean,
      default: false,
    },
    filled: {
      type: Boolean,
      default: false,
    },
    fullWidth: {
      type: Boolean,
      default: false,
    },
    flat: {
      type: Boolean,
      default: false,
    },
    light: {
      type: Boolean,
      default: false,
    },
    validateOnBlur: {
      type: Boolean,
      default: false,
    },
    outlined: {
      type: Boolean,
      default: false,
    },
    dense: {
      type: Boolean,
      default: false,
    },
    persistentHint: {
      type: Boolean,
      default: false,
    },
    readonly: {
      type: Boolean,
      default: false,
    },
    error: {
      type: Boolean,
      default: false,
    },
    success: {
      type: Boolean,
      default: false,
    },
    shaped: {
      type: Boolean,
      default: false,
    },
    rounded: {
      type: Boolean,
      default: false,
    },
    value: {
      type: [String, Object],
      default: "",
    },
    label: {
      type: String,
    },
    rules: {
      type: Array,
      default() {
        return [];
      }
    },
  },
  data() {
    return {
      countryList: [],
      country: "",
      countries,
    };
  },
  methods: {
    selectCountry() {
      this.$emit("input", this.country);
      EventBus.$emit("countryValue", this.country);
    },
  },
};
</script>