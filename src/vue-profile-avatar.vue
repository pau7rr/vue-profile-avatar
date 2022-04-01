<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProfileAvatar', 
  props: {
    username: { type: String, required: true },
    size: { type: String, default: 's', required: false },
    border: { type: Boolean, default: true, required: false },
    bgColor: { type: String, required: false },
    borderColor: { type: String, required: false },
    textColor: { type: String, required: false },
  },
  data() {
    return {
       arrBackgroundColors: {
        a: '#FF6633', b: '#FFB399', 
        c: '#FF33FF', d: '#FFFF99', 
        e: '#00B3E6', f: '#E6B333',
        g: '#3366E6', h: '#999966',
        i: '#99FF99', j: '#B34D4D',
        k: '#80B300', l: '#809900', 
        m: '#E6B3B3', n: '#6680B3', 
        o: '#66991A', p: '#FF99E6', 
        q: '#CCFF1A', r: '#FF1A66', 
        s: '#E6331A', t: '#33FFCC', 
        u: '#66994D', v: '#B366CC', 
        w: '#4D8000', x: '#B33300', 
        y: '#CC80CC', z: '#66664D', 
        1: '#4D8066', 2: '#809980', 
        3: '#E6FF80', 4: '#1AFF33', 
        5: '#999933', 6: '#FF3380', 
        7: '#CCCC00', 8: '#66E64D', 
        9: '#4D80CC', 0: '#9900B3', 
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
    },
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
      if (this.bgColor) return this.bgColor

      return this.arrBackgroundColors[initial.toLowerCase()]
    },
    getBorderColor(color, percent) {
      if (this.borderColorPropExists()) return this.borderColor

      return this.shadeColor(color, percent)
    },
    getTextColor(color, percent) {
      if (this.textColorPropExists()) return this.textColor

      return this.shadeColor(color, percent)
    },
    shadeColor(color, percent) {
      var R = parseInt(color.substring(1,3),16);
      var G = parseInt(color.substring(3,5),16);
      var B = parseInt(color.substring(5,7),16);

      R = parseInt(R * (100 + percent) / 100);
      G = parseInt(G * (100 + percent) / 100);
      B = parseInt(B * (100 + percent) / 100);

      R = (R<255)?R:255;  
      G = (G<255)?G:255;  
      B = (B<255)?B:255;  

      var RR = ((R.toString(16).length==1)?"0"+R.toString(16):R.toString(16));
      var GG = ((G.toString(16).length==1)?"0"+G.toString(16):G.toString(16));
      var BB = ((B.toString(16).length==1)?"0"+B.toString(16):B.toString(16));

      return "#"+RR+GG+BB;
    },
    borderColorPropExists() {
      if (this.borderColor) return true
      return false
    },
    textColorPropExists() {
      if (this.textColor) return true
      return false
    }
  },
});
</script>

<template>
  <div 
    class="avatarContainer" 
    :class="[avatarClass, isBorder]" 
    :style="{ 
      backgroundColor: backgroundColor, 
      color: getTextColor(backgroundColor, -45), 
      borderColor: getBorderColor(backgroundColor, -45),
    }"
  >
    <span class="text"> {{initials}} </span>
  </div>
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@600&display=swap');

  .avatarContainer {
    display: flex;
    border-radius: 100%;
    background-color: #6666FF;
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
