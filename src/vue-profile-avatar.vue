<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProfileAvatar', 
  props: {
    username: { type: String, required: true },
    size: { type: String, default: 's', required: false },
    border: { type: Boolean, default: true, required: false }
  },
  data() {
    return {
       arrBackgroundColors: {
        a: '#FF6633' ,
        b: '#FFB399' , 
        c: '#FF33FF', 
        d: '#FFFF99', 
        e: '#00B3E6', 
        f: '#E6B333',
        g: '#3366E6', 
        h: '#999966',
        i: '#99FF99', 
        j: '#B34D4D',
        k: '#80B300',
        l: '#809900', 
        m: '#E6B3B3',
        n: '#6680B3', 
        o: '#66991A', 
        p: '#FF99E6', 
        q: '#CCFF1A', 
        r: '#FF1A66', 
        s: '#E6331A',
        t: '#33FFCC', 
        u: '#66994D', 
        v: '#B366CC', 
        w: '#4D8000', 
        x: '#B33300', 
        y: '#CC80CC', 
        z: '#66664D',
        '_': '#991AFF',
        '@': '#E666FF',
        '!': '#4DB3FF', 
        '#': '#1AB399', 
        '-': '#E666B3', 
        '/': '#33991A', 
        '=': '#CC9999', 
        '-': '#B3B31A', 
        '+': '#00E680', 
        1: '#4D8066', 
        2: '#809980', 
        3: '#E6FF80', 
        4: '#1AFF33', 
        5: '#999933', 
        6: '#FF3380', 
        7: '#CCCC00', 
        8: '#66E64D', 
        9: '#4D80CC', 
        0: '#9900B3', 
        else: '#6666FF'
      }
    };
  },
  computed: {
    avatarClass() {
      return {
        'small': this.size === 's',
        'medium': this.size === 'm',
        'large': this.size === 'l',
      }
    },
    isBorder() {
      return {
        'border': this.border,
      }
    },
    initials() {
      this.backgroundColor
      return this.getInitials(this.username)
    },
    backgroundColor() {
      return this.getColorByInitial(this.getInitials(this.username)[0])
    }
  },
  methods: {
    getInitials(username) {
      const usernameParts = username.split(' ')

      const initials = usernameParts.map((e) => {
        return e.slice(0, 1).toUpperCase()
      })

      if (initials.length > 3) return initials.slice(0, 3).join('')

      return initials.join('')
    },
    getColorByInitial(initial) {
      return this.arrBackgroundColors[initial.toLowerCase()]
    }
  },
});
</script>

<template>
  <div class="avatarContainer" :class="[avatarClass, isBorder]" :style="{backgroundColor: backgroundColor}">
    <span class="text"> {{initials}} </span>
  </div>
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@600&display=swap');

  .avatarContainer {
    display: flex;
    border-radius: 100%;
    background-color: #FF6633;
  }

  .small {
    height: 50px;
    width: 50px;
  }
  
  .medium {
    height: 75px;
    width: 75px;
  }
  
  .large {
    height: 100px;
    width: 100px;
  }

  .text {
    margin: auto;
    font-family: 'Montserrat', sans-serif;
  }

  .border {
    border: 2px solid black;
  }
</style>
