<template>
    <q-layout view="lHh Lpr lFf">
        <!-- <q-header reveal style="background-color: #202124"> -->
        <q-header
            reveal
            v-scroll="scrolled"
            :style="
                filled_header >= 20
                    ? 'background-color: #202124'
                    : 'background-color: transparent'
            "
        >
        <q-toolbar class="column">
            <!-- <button class="app-back">
              <q-icon
                size="20px"
                color="white"
                name="mdi-keyboard-backspace"
              ></q-icon>
              <div class="app-back__label">Back</div>
            </button> -->
            <div class="app-gateway-search">
                <q-icon size="20px" name="search"></q-icon>
                <input type="text" placeholder="Search" />
            </div>
        </q-toolbar>
        </q-header>
        <q-page-container class="app-gateway-container">
            <div class="watermark">SAMPLE</div>
            <router-view />
        </q-page-container>
    </q-layout>
</template>

<script>
export default {
    name: "MyLayout",

    data() {
        return {
            filled_header: 20
      };
    },
    methods: {
        scrolled(position) {
            this.filled_header = position;
        }
    },
    mounted() {
        this.scrolled();
    }
};
</script>

<style lang="scss">

.swiper-preloader {
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -21px;
    margin-top: -21px;
    z-index: 10;
    transform-origin: 50%;
}

.app-back {
    background-color: transparent;
    border: 0;
    padding: 0;
    display: flex;
    align-items: center;
    align-self: flex-start;
    margin-top: 0.5rem;
    outline: none;

    &__label {
         color: white;
         font-size: 14px;
         margin-left: 0.5rem;
     }
}

.app-gateway-search {
    position: relative;
    display: flex;
    margin-top: 1rem;
    width: 100%;

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
        width: 100%;
        padding: 8px 16px 8px 30px;
        outline: none;
        color: white;
        font-size: 0.75rem;
    }
}

.app-gateway-container {
    position: relative;
    background-color: #111010;

    .watermark {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) rotate(-20deg);
        font-size: 5rem;
        font-weight: 700;
        color: rgba(#fff, .3);
        z-index: 50;
        pointer-events: none;
    }

    &::before {
        content: " ";
        background: linear-gradient(rgba(#000, 0.4), rgba(#000, 0.4));
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 2;
    }
}
</style>
