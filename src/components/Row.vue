<template lang="html">
  <tr>
    <td class="col-md-1"><input type="text" class="form-control input-sm" placeholder="Count" v-model="cropCount"></input></td>
    <td class="col-md-1">{{ crop.name }}</td>
    <td class="col-md-1"><input type="text" class="form-control input-sm" placeholder="Price" v-model="rewardPrice"></input></td>
    <td class="col-md-1 text-center">{{ crop.level.min }}</td>
    <td class="col-md-1 text-center">{{ crop.level.max }}</td>
    <td class="col-md-1">{{ crop.reward.first.name }}</td>
    <td class="col-md-1 text-center">{{ firstReward }}</td>
    <td class="col-md-1">{{ crop.reward.second.name }}</td>
    <td class="col-md-1 text-center">{{ secondReward }}</td>
  </tr>
</template>

<script>
export default {
  name: 'row',
  props: ['crop', 'mode'],
  data () {
    return {
      cropCount: '',
      rewardPrice: ''
    }
  },
  computed: {
    firstReward: function () {
      return parseInt(this.rewardPrice / this.crop.reward.first.value * this.cropCount, 10)
    },
    secondReward: function () {
      return parseInt(this.rewardPrice / this.crop.reward.second.value * this.cropCount, 10)
    }
  }
}
</script>

<style lang="css"
  
</style>
