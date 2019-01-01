 <template>
  <div id="app">
    <kendo-datasource
      ref="dataSource"
      :transport-read-url="'https://api.iextrading.com/1.0/stock/market/list/gainers'"
      :transport-read-data-type="'json'">
    </kendo-datasource>
    <kendo-chart
      :data-source-ref="'dataSource'"
      :title="title"
      :legend="legend"
      :tooltip="tooltip"
      :series="series"
      :theme="'material'">
    </kendo-chart>
  </div>
</template>


<script>
export default {
  name: 'app',
  data () {
    return {
     title: {
      text: 'Market cap'
     },
     legend: {
      position: 'top'
     },
     tooltip: {
      visible: true,
      format: '${0:N}',
      
     },
     series: [{
      type: 'donut',
      field: 'marketCap',
      categoryField: 'symbol',
      labels: {
        visible: true,
        template: '#: category #'
      }
     }]
    }
  }
}
</script>


<style>
#app {
  margin-top: 60px;
}

</style>
