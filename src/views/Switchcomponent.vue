<template>
  <v-row justify="center">
    <v-col cols="6">
      <v-row justify="center" v-for="(item, index) in devices" :key="index">
        <v-col cols="3" align="center">
          <p>Devicename: {{ item.deviceName }}</p>
        </v-col>
        <v-col cols="4">
          <v-switch
            :value="true"
            :input-value="item.deviceState == 'ON' ? true : false"
            @change="toggle(item.deviceName, item.deviceState)"
            color="success"
            class="pl-8"
          ></v-switch>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require("axios");

export default {
  name: "switchComponent",
  data() {
    return {
      DeviceName: "",
      switch1: false,
      body: {
        MAC_ID: 1,
      },
      devices: [],
    };
  },
  mounted() {
    axios.post("http://localhost:5000/getDevice", this.body).then((data) => {
      console.log(data, "received data");
      this.devices = data.data.devices;
      console.log(this.devices);
    });
  },
  methods: {
    toggle(deviceName, state) {
      console.log(deviceName, "DeviceName", state);
      axios.post("http://localhost:5000/changeState", {
        MAC_ID: 1,
        deviceName: deviceName,
        deviceState: state == 'ON' ? 'OFF': 'ON'
      }).then((data) => {
      console.log(data, "received data");
      this.devices = data.data.devices;
      console.log(this.devices);
    });
    }
  }
};
</script>
