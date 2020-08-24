<template>
  <div id="footer">
    <b-row align-v="end">
      <b-col>
        Created by:
        <p>Halvor Nafstad</p>
      </b-col>
      <b-col>
        Contact:
        <p>mrnafstad@gmail.com</p>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
#footer {
  background-color: #e8e8e8;
  position: relative;
  width: 100%;
  font-size: 75%;
  bottom: 0%;
}

.align-items-end {
  width: 100%;
  padding: 1%;
}
</style>