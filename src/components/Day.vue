<template>
  <div class="day">
    <h1 class="day-title">
      {{ $route.params.date }}
    </h1>
    <ul class="day-list">
      <li v-for="list in items" :key="list.id"
      class="day-list-item">
        <div class="time">
          <h2>
            {{list.id}}
          </h2>
        </div>

        <div class="action">
          <input type="text" placeholder="한 일을 작성해주세요"
          v-model="list.action">
        </div>
        <day-score
        @onUpdateScore="onUpdateScore"
        :list="list"
        >

        </day-score>
        <div class="note">
          <textarea v-model="list.note" placeholder="노트를 작성해주세요"></textarea>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import DayScore from './DayScore'
export default {
  name: 'Day',
  data(){
    return{
      items:[
        {
          action: "",
          id: "2018-04-01-08-10",
          note: "",
          open: false,
          score: undefined
        },
        {
          action: "",
          id: "2018-04-01-10-12",
          note: "",
          open: false,
          score: undefined
        },
        {
          action: "",
          id: "2018-04-01-12-14",
          note: "",
          open: false,
          score: undefined
        }
      ]
    }
  },
  methods:{
    onUpdateScore(list,score){
      list.score = score;

    }
  },
  props: {

  },
  components:{
    DayScore
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
