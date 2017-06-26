<template lang="html">
  <div id="manor">
    <div class="table-responsive">
    <table class="table table-striped table-bordered">
      <tr>
        <td colspan="3" class="col-md-1 text-center">Seed</td>
        <td colspan="2" class="col-md-1 text-center">Level Range</td>
        <td colspan="4" class="col-md-1 text-center">Rewards</td>
      </tr>
      <tr>
        <td colspan="3"><input type="text" class="form-control input-sm" placeholder="Name filter" v-model="nameFilter"></input></td>
        <td colspan="2"><input type="text" class="form-control input-sm" placeholder="Level filter" v-model="levelFilter"></input></td>
        <td colspan="4"><input type="text" class="form-control input-sm" placeholder="Reward filter" v-model="rewardFilter"></input></td>
      </tr>
      <tr>
        <td rowspan="2" class="col-md-1 text-center">Count</td>
        <td rowspan="2" class="col-md-1 text-center">Name</td>
        <td rowspan="2" class="col-md-1 text-center">Buy price</td>
        <td rowspan="2" class="col-md-1 text-center">Min</td>
        <td rowspan="2" class="col-md-1 text-center">Max</td>
        <td colspan="2" class="col-md-1 text-center">First</td>
        <td colspan="2" class="col-md-1 text-center">Second</td>
      </tr>
      <tr>
        <td class="text-center">Material</td>
        <td class="text-center">Receive</td>
        <td class="text-center">Material</td>
        <td class="text-center">Receive</td>
      </tr>
      <tbody>
        <row  v-for="crop in filtered" :crop="crop"></row>
      </tbody>
      <tr v-if="filtered.length === 0">
        <td colspan="9" class="text-center">No records found</td>
      </tr>
    </table>
    </div>
  </div>
</template>

<script>
import manor from 'assets/manor.json'
import Row from 'components/Row'

export default {
  name: 'manor',
  props: ['mode'],
  data () {
    return {
      manor: manor,
      nameFilter: '',
      levelFilter: '',
      rewardFilter: ''
    }
  },
  computed: {
    filtered: function () {
      return this.manor.filter((e) => {
        return (!this.nameFilter || this.nameFilter.length === 0) || e.name.toLowerCase().indexOf(this.nameFilter.toLowerCase()) !== -1
      }).filter((e) => {
        return (!this.levelFilter || this.levelFilter.length === 0) || (e.level.min <= this.levelFilter && e.level.max >= this.levelFilter)
      }).filter((e) => {
        return (!this.rewardFilter || this.rewardFilter.length === 0) || (e.reward.first.name.toLowerCase().indexOf(this.rewardFilter.toLowerCase()) !== -1) || (e.reward.second.name.toLowerCase().indexOf(this.rewardFilter.toLowerCase()) !== -1)
      })
    }
  },
  components: {
    Row
  }
}
</script>

<style lang="css">
</style>
