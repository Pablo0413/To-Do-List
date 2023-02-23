<template>
  <div class="home">
    <b-jumbotron id="legend">
      <h1 class="text-uppercase">to do list</h1>
      <p>made by Pavlo Shubalyi</p>
    </b-jumbotron>
  </div>
</template>

<script>

export default {
  name: 'Home',
}
</script>

<style>
#legend {
  background-color: #132524;
}

#legend h1 {
  color: #FEEDE1;
  font-weight: 700 !important;
  font-size: 11rem !important;
}

#legend p {
  color: #FEEDE1;
  font-weight: 400 !important;
  font-size: 20px !important;
}

.home {
  height: calc(100vh - 56px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  #legend h1 {
    color: #FEEDE1;
    font-weight: 700 !important;
    font-size: 5rem !important;
  }
}
</style>