<script setup>
import {onMounted, reactive} from 'vue'

    const data = reactive([])
    const arr  = reactive([
        "First Title",
        "Second Title",
        "Third Title",
        "Fourth Title",
        "Fifth Title",
        "Sixth Title",
        "Seventh Title",
        "Eighth Title",
        "Nineth Title",
        "Tenth Title"
      ])

    function getPart() {

      for(let i = 0; i < 10; i++) {
        data.push({
          title: arr[i],
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam adipisci quam facilis, in, eos libero earum, nihil vel sint maiores officia dicta repellat laboriosam culpa? Cupiditate amet rem non dolor."
        })
      }
    }
      
    function scrolling() {

      if(window.scrollY + window.innerHeight >= document.body.scrollHeight - 50) {
        for(let i = 0; i < arr.length; i++) {
          data.push({
          title: arr[i],
          desc: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Placeat, optio cupiditate. Error in maiores inventore, minus itaque optio fugit quo debitis ipsum dicta enim nesciunt dolor vel aperiam odio nihil.'
        })
        }
      }
    }

    onMounted(()=> {
      getPart()
      window.addEventListener('scroll', scrolling)
    })
</script>

<template>
 <section>
    <h2>Infinite Scroll</h2>
    <div class="main" v-for="(part, index) in data" :key="index">
      <h2>{{part.title}}</h2>
      <p>
        {{part.desc}}
      </p>
    </div>
 </section>
</template>


<style>
#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  background-color: #eee;
  padding: 10px 15px;
  width: 80%;
  margin: 20px auto;
  border-radius: 5px;
}
.main h2 {
  color: #00c7bd;
}
.main p {
  text-align: left;
  line-height: 2;
}
</style>