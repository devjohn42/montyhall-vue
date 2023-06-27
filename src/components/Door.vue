<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: isSelected && !isOpen }">
      <!--caso verdadeiro o selected é aplicado como classe-->
      <Gift v-if="isOpen && hasGift" />
    </div>
    <div
      class="door"
      :class="{ open: isOpen }"
      @click="isSelected = !isSelected"
    >
      <div class="number" :class="{ selected: isSelected }">{{ number }}</div>
      <div
        class="knob"
        :class="{ selected: isSelected }"
        @click="isOpen = true"
      ></div>
    </div>
  </div>
</template>

<script>
import Gift from "./Gift.vue";
export default {
  name: "Door",
  components: { Gift },
  props: {
    number: {},
    hasGift: { type: Boolean },
  },
  data: () => {
    return {
      isOpen: false,
      isSelected: false,
    };
  },
};
</script>

<style scoped>
/* 
com o scoped não é possível utilizar o root para definir variáveis...
*/
.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #a52a2a;
  margin-bottom: 20px;
  font-size: 3rem;

  display: flex;
  justify-content: center;
}

.door-frame {
  position: absolute;
  height: 300px;
  width: 180px;

  border-left: 5px solid #2aa55d;
  border-top: 5px solid #2aa55d;
  border-right: 5px solid #2aa55d;

  display: flex;
  align-items: flex-end;
  justify-content: center;
}

.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: #2d2d2d;

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15px;

  cursor: pointer;
}

.door .number {
  color: #2aa55d;
}

.door .knob {
  height: 20px;
  width: 20px;
  margin-top: 60px;
  border-radius: 10px;
  background-color: #2aa55d;
  align-self: flex-start;
  cursor: grab;
}

.door-frame.selected {
  border-left: 5px solid #13e269;
  border-top: 5px solid #13e269;
  border-right: 5px solid #13e269;
}

.door .number.selected {
  color: #13e269;
}

.door .knob.selected {
  background-color: #13e269;
}

.door.open {
  background-color: #0007;
}

.door.open .knob,
.door.open .number {
  display: none;
}
</style>
