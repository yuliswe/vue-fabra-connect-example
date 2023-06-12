

<script lang="ts">
import { FabraConnect } from "@fabra/vue-fabra-connect";
export default {
  components: {
    FabraConnect,
  },
  data: () => ({
    containerID: "fabra-connect-container",
    theme: {
      colors: {
        primary: {
          base: "red"
        }
      }
    },
    linkToken: "eyJhbGciOiJLTVNIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbl9pbmZvIjp7Im9yZ2FuaXphdGlvbl9pZCI6NDEsImVuZF9jdXN0b21lcl9pZCI6ImFiY2QtMTIzNC1lZmdoLTU2NzgiLCJkZXN0aW5hdGlvbl9pZHMiOm51bGx9LCJleHAiOjE2ODY2MDkxMzYsImlhdCI6MTY4NjYwNTUzNn0.H4t27FUXg8JAD5x02Bqa1Bs8OA9Zx8dAmM-PkP2b-Ic",
  }),
  methods: {
    close() {
      (this.$refs.FabraConnect as typeof FabraConnect).close();
    },
    switchContainer() {
      this.containerID = this.containerID === "fabra-connect-container" ? "fabra-connect-container-2" : "fabra-connect-container";
    },
    switchTheme() {
      if (this.theme.colors.primary.base === "blue") {
        this.theme = {
          colors: {
            primary: {
              base: "red"
            }
          }
        }
      } else {
        this.theme = {
          colors: {
            primary: {
              base: "blue"
            }
          }
        }
      }
    },
  }
}
</script>

<template>
  <div class="flex">
    <div id="fabra-connect-container" class="box">#fabra-connect-container</div>
    <div id="fabra-connect-container-2" class="box">#fabra-connect-container-2</div>
  </div>
  <fabra-connect :containerID="containerID" ref="FabraConnect" :customTheme="theme"
    :linkToken="linkToken"></fabra-connect>

  <fabra-connect :containerID="containerID" ref="FabraConnect" :customTheme="theme" :linkToken="linkToken">

    <template #button="props">
      <button @click="props.onClick">Open Fabra Connect Override</button>
    </template>
  </fabra-connect>
  <button @click="close">Close</button>
  <button @click="switchContainer">Switch Container</button>
  <button @click="switchTheme">Switch Theme</button>
</template>

<style scoped>
.flex {
  display: flex;
}

.box {
  border: 1px solid black;
}

#fabra-connect-container {
  width: 500px;
  height: 500px;
}

#fabra-connect-container-2 {
  width: 500px;
  height: 500px;
}
</style>
