<template>
  <div class="hello">
    <h1>`Hello world {{ msg }}`</h1>
    <new :msg="msg">

    </new>
    <h2>{{ author }}</h2>
    <h3>age : {{ age + 10 }}</h3>
    <p v-html="article"></p>
    <p v-if="seen">보인다</p>
    <p v-else>보이지 않음</p>
    <p v-show="seen">show</p>
    <p v-show="!seen">NOT show</p>
    <a :href="url">google</a>

    <p :class="{active: isActive}">active</p>
    <p :style="{color:textColor}">스타일 바인드</p>
    <ul>
      <li v-for="item in items" :key="item.name">
        {{ item.name }} - {{ item.age }}
      </li>
    </ul>
    <ul>
      <li v-for="(value,keyyyy,index) in person" :key="index">
        {{ value }}
      </li>
    </ul>

    <button @click.once="updateScore(2)">클릭하세요</button>
    <input type="text" @keyup.enter="keyup()">
    <h1>score:{{ score }}</h1>

    <h2>오늘 : {{ today }}</h2>

    <h1>{{ msg }}</h1>
    <input type="text" placeholder="입력하세요" v-model="msg">
    <input type="checkbox" v-model="seen">
    <p>{{ seen }}</p>

    <input type="radio" v-model="age" value="30">
    <input type="radio" v-model="age" value="20">
    <input type="radio" v-model="age" value="10">
    <p>{{ age }}</p>

    <select v-model="age">
      <option value="30">30</option>
      <option value="20">20</option>
      <option value="10">10</option>
    </select>
  </div>
</template>

<script>
import New from './New';
export default {
  name: 'HelloWorld',
  components:{
    New
  },
  data(){
    return{
      score:0,
      msg:"반갑습니다!",
      author:"김동국",
      age:20,
      article: `<strong>Hello</strong> world!`,
      seen:true,
      url:"http://www.google.com",
      isActive: false,
      textColor: 'red',
      items:[
        {name:'red', age:15}
        ,{name:'blue',age:25}
        ,{name:'green',age:30}
      ],
      person:{
        name:'bob',
        age: 25,
        location: 'seoul'
      }

    }
  },
  methods:{
    updateScore(score){
      console.log(score);
      this.score = score;
    },
    keyup(){
      console.log('keyup');
    }
  },
  computed:{
    today(){
      let date = new Date();
      return date.getDate();
    }
  },
  // props: {
  //   msg: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
