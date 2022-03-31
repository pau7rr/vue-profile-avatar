<script>
import { defineComponent } from 'vue';
import ProfileAvatar from '@/vue-profile-avatar.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    ProfileAvatar
  }
});
</script>

<template>
  <div id="app">
    <profile-avatar username="pau7rr" />
  </div>
</template>
