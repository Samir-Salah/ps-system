<template>
  <div class="header-panel">
    <div class="header-logo container">
      {{ shopFirstName }} <span> {{ shopLastName }}</span>
    </div>
    <div class="logout-side">
      <button class="logout-btn">Logout</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data: function() {
    return {
      shopFirstName: "Shop",
      shopLastName: "Name"
    };
  }
};
</script>
