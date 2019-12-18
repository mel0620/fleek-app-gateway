<template>
  <q-layout view="lHh Lpr lFf">
    <q-header reveal style="background-color: transparent">
      <q-toolbar class="column">
        <button class="app-back">
          <q-icon
            size="20px"
            color="white"
            name="mdi-keyboard-backspace"
          ></q-icon>
          <div class="app-back__label">Back</div>
        </button>
        <div class="app-gateway-search">
          <q-icon size="20px" name="search"></q-icon>
          <input type="text" placeholder="Search" />
        </div>
      </q-toolbar>
    </q-header>

    <router-view />
  </q-layout>
</template>

<script>
export default {
  name: "MyLayout",

  data() {
    return {
      leftDrawerOpen: false
    };
  }
};
</script>

<style lang="scss">
.app-back {
  background-color: transparent;
  border: 0;
  padding: 0;
  display: flex;
  align-items: center;
  align-self: flex-start;
  margin-top: 0.5rem;

  &__label {
    color: white;
    font-size: 12px;
    margin-left: 0.5rem;
  }
}

.app-gateway-search {
  position: relative;
  display: block;
  margin-top: 0.5rem;

  .q-icon {
    position: absolute;
    top: 50%;
    left: 8px;
    transform: translateY(-50%);
    opacity: 0.5;
  }

  input {
    background-color: rgba(255, 255, 255, 0.2);
    border-radius: 50px;
    border: 0;
    min-width: 300px;
    padding: 4px 16px 4px 30px;
    outline: none;
    color: white;
  }
}
</style>
