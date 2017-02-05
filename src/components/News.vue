<template>
<div class="news">
  <div>
    <div class="jumbotron">
      <h2><span class="glyphicon glyphicon-list-alt"></span>&nbsp;Cricket Calendar</h2>
      <table class="table table-striped">
        <thead>
          <tr class="info">
            <th>Name</th>
            <th>Date</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="match in matches">
            <td>{{match.name}}</td>
            <td>{{match.date}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'news',
  data() {
    return {
      matches: []
    }
  },
  created: function() {
    this.$http.get('http://cricapi.com/api/matchCalendar?apikey=hfrDfOnDgIcSUAKzXxMbgTXi89H2')
      .then(response => {
        this.matches = response.data.data;
        console.log(this.matches);
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
