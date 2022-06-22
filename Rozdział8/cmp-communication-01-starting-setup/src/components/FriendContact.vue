<template>
  <li>
    <h2>{{ name }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorite"> {{isFavorite === '1' ? 'unset':'set'}} favorite </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAdress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
    //props: ["name", "phoneNumber", "emailAdress"],
    props:{
      name: {
        type:String,
        required: true
      },
      phoneNumber: {
        type:String,
        required: true
      },
      emailAdress: {
        type:String,
        required: true
      },
      isFavorite: {
        type:Boolean,
        required: false,
        default: false,
      }
    },
  data() {
    return {
      detailsAreVisible: false,
      friendisFavorite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
        this.friendisFavorite = !this.friendisFavorite;
    }
  }
};
</script>