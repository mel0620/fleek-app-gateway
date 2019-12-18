<template>
  <q-layout view="lHh Lpr lFf">
    <q-header reveal style="background-color: #202124">
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
    <q-page-container class="app-gateway-container">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MyLayout",

  data() {
    return {};
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
    font-size: 14px;
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
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 50px;
    border: 0;
    min-width: 300px;
    padding: 8px 16px 8px 30px;
    outline: none;
    color: white;
    font-size: 0.75rem;
  }
}

.app-gateway-container {
  position: relative;
  //   background-color: #111010;

  //   &::before {
  //     content: " ";
  //     background: linear-gradient(rgba(#000, 0.4), rgba(#000, 0.4));
  //     position: absolute;
  //     top: 0;
  //     left: 0;
  //     right: 0;
  //     bottom: 0;
  //     z-index: 2;
  //   }
}
</style>
