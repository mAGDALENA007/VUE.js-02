<template>
  <div id="app">
    <date-picker v-model="date" lang="em" type="date" format="YYYY-MM"></date-picker>
  </div>
</template>

<script>
  import DatePicker from 'vue2-datepicker';
  import 'vue2-datepicker/index.css';
 
  export default {
    components: { DatePicker },
    data() {
      return {
        time1: null,
        time2: null,
        time3: null,
      };
    },
  };
</script> 
 
<template>
  <div>
    <!--<date-picker v-model="time1" valueType="format"></date-picker>-->
    <date-picker v-model="time2" type="datetime"></date-picker>
    <!--<date-picker v-model="time3" range></date-picker>-->
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
