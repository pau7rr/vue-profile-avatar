<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProfileAvatar', 
  props: {
    username: { type: String, required: true },
    size: { type: String, default: 's', required: false },
    border: { type: Boolean, default: true, required: false }
  },
  computed: {
    avatarClass() {
      return {
        'small': this.size === 's',
        'medium': this.size === 'm',
        'large': this.size === 'l',
      }
    },
    isBorder() {
      return {
        'border': this.border,
      }
    },
    initials() {
      return this.getInitials(this.username)
    }
  },
  methods: {
    getInitials(username) {

    }
  },
  data() {
    return {
      
    };
  },
});
</script>

<template>
  <div class="avatarContainer" :class="[avatarClass, isBorder]">
    <span class="text"> PR </span>
  </div>
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@600&display=swap');

  .avatarContainer {
    display: flex;
    border-radius: 100%;
    background-color: cornflowerblue;
  }

  .small {
    height: 50px;
    width: 50px;
  }
  
  .medium {
    height: 75px;
    width: 75px;
  }
  
  .large {
    height: 100px;
    width: 100px;
  }

  .text {
    margin: auto;
    font-family: 'Montserrat', sans-serif;
  }

  .border {
    border: 2px solid black;
  }
</style>
