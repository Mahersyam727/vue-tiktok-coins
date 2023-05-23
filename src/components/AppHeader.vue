<script>
import AppLogo from './AppLogo.vue';
import AppSearch from './AppSearch.vue';
import AppActions from './AppActions.vue';

export default {
  name: 'Header',
  components: { AppLogo, AppSearch, AppActions },
};
</script>

<template>
  <div class="tiktok-xk7ai4-DivHeaderContainer e10win0d0">
    <div class="tiktok-notu47-DivHeaderWrapperMain e10win0d1">
      <!-- Logo -->
      <app-logo />
      <!-- Search -->
      <app-search />
      <!-- Actions -->
      <app-actions />
    </div>
  </div>
</template>
