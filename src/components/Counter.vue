<script setup>
import { ref, toRefs, watch } from 'vue'

var props = defineProps({
  msg: String,
  count: String
})
props = toRefs(props)

var counter = props.count.value ? ref(props.count.value) : ref(0)

watch(props.count, function (newVal) {
  typeof (props.count.value) != "undefined" ? counter.value = newVal : counter.value = 0
})

function counterIncr() {
  if (props.count) {
    counter.value++
  } else {
    counter++
  }
}
</script>

<template>
  <div class="container" id="wpwrap">
    <div class="element">
      <span>
        {{ counter }}
      </span>
      <h1>
        {{ msg }}
      </h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi eius dolorem quam, delectus, facilis veritatis
        deserunt quod recusandae maxime voluptatem quaerat quo perferendis illum praesentium nihil repellendus quas
        explicabo assumenda ipsam iure voluptatum! Quidem beatae reiciendis, minus iusto dolore doloribus.
      </p>
      <div class="buttons">
        <input @click="counter = count ? count : 0" type="button" value="Reset Me">
        <input @click="counterIncr" type="button" value="Count Me">
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 70%;
  height: auto;
  margin: auto;

  h1 {
    color: azure;
    user-select: none;
    /* font-weight: 700; */
  }

  p {
    margin-bottom: 50px;
    padding: 0px 100px;
  }

  span {
    font-size: 64px;
    font-weight: 700;
    color: lightgray;
  }

  .buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 50px;

    input {
      display: inline-block;
      padding: 15px 40px;
      background-color: lightblue;
      border: none;
      cursor: pointer;
      color: grey;
      font-weight: 700;
      border-radius: 5px;
    }

    input:hover {
      scale: 1.05;
      transition: ease .5s all;
      color: black;
      border: none;
    }
  }
}
</style>