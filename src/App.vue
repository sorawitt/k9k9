<template>
  <div id="app" :style="{background: gradient}">
    
    <h1>Hello fucking world</h1>
    <vue-typer :text=msg :repeat='0'></vue-typer>
    <button v-on:click="onRandomBtnClicked">Press me :)</button>
    <Todos v-bind:todos="todos"/>
  </div>
</template>

<script>
import Todos from './components/Todos'
import { VueTyper } from 'vue-typer'

export default {
  name: 'app',
  components: {
    Todos,
    VueTyper
  },
  data() {
    return {
      msg: "Hello Fucking world!",
      todos: [
        {
          id: 1,
          title: "แดกเหล้ารอบวงจ้า"
        },
        {
          id: 2,
          title: "เพียวสามฝา"
        },
        {
          id: 3,
          title: "ให้เพื่อนถามอะไรก็ได้ 1 ข้อ หรือกินเพียวสามฝา"
        }
      ],
      colors: [
        {
          id:0, 
          hex:'#f12711'
        }, 
        {
          id:1, 
          hex:'#f5af19'
        }
      ],
      id: 2
    }
  },
  methods: {
    onRandomBtnClicked() {
      this.generateGradient()
      let numberRandom = Math.floor(Math.random() * this.todos.length)
      this.msg = this.todos[numberRandom].title
    },
		generateGradient(){
			for(let i=0;i<this.colors.length;i++){
          this.colors[i].hex = this.randomHex()
      }
		},
		lockColor(index) {
			this.colors[index].disabled === true ?
				this.colors[index].disabled = false : 
				this.colors[index].disabled = true
		},
		randomHex() {
			return '#'+Math.random().toString(16).slice(2, 8)
		}
  },
  mounted() {
    this.generateGradient()
  },
	computed: {
		gradient() {
			let colors = 'linear-gradient(45deg'
			this.colors.forEach(function(e){  
				colors += ',' + e.hex
			});
			colors += ')'
			return colors
		}
	}
}
</script>

<style scope>


html, body {
  height: 100%;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  display: flex;
  height: 100%;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  transition: background-color 6s;
}

/* Buttons styles start */
button {
    display: inline-block;
    border: none;
    padding: 1rem 2rem;
    margin: 0;
    text-decoration: none;
    background: #111111;
    color: white;
    font-family: sans-serif;
    font-size: 1rem;
    line-height: 1;
    cursor: pointer;
    text-align: center;
    transition: background 250ms ease-in-out, transform 150ms ease;
    -webkit-appearance: none;
    -moz-appearance: none;
}

button:hover,
button:focus {
    background: #111111;
}

button:focus {
    outline: 1px solid #111111;
    outline-offset: -4px;
}

button:active {
    transform: scale(0.99);
}
/* Button styles end */
.vue-typer {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 63px;

}

</style>
