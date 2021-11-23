<template>
  <v-row justify="center">
    <v-col cols="6">
      <v-card height="300" width="400" class="mt-10 mb-10" elevation="2">
        <v-card-text class="text-h5 mb-1"> Devicename: {{ DeviceName }} </v-card-text>
        <v-row>
          <v-col>

          </v-col>
        </v-row>
        <v-row justify="center" align="center">
          <v-col cols="4">
            <v-switch v-model="switch1" color="success" class="pl-8"></v-switch>
          </v-col>
        </v-row>
        
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "switchComponent",
  data() {
    return {
      DeviceName: "",
      switch1: false,
    };
  },
  mounted() {
    
  }
};
</script>
