<template>
  <card style="width: 400px; margin: auto" class="card-container">
    <cardHeader>
      <cardTitle class="card-title"
        >Shopping List <span class="k-icon k-i-cart"></span
      ></cardTitle>
    </cardHeader>
    <cardBody>
      <div class="list">
        <li v-for="(list, index) in lists" :key="index" :class="{ removed: list.checked }">
          <div class="form-box">
            <input type="checkbox" v-model="list.checked" class="input-box" />

            <label class="label">
              {{ list.text }}
            </label>
            <span class="k-icon k-i-trash" v-on:click="removeList(index)"></span>
          </div>
        </li>
      </div>
    </cardBody>
    <cardFooter class="footer-section">
      <div class="col-xs-12 col-md-6 example-col">
        <KInput
          :style="{ width: '230px' }"
          v-model="currentList"
          v-on:keyup.enter="addList"
        ></KInput>
      </div>
      <div class="col-xs-12 col-md-6 example-col">
        <kbutton
          :theme-color="'primary'"
          :style="{ width: '100px' }"
          @click="addList"
          >Add List</kbutton
        >
      </div>
    </cardFooter>
  </card>
</template>

<script>
import {
  Card,
  CardHeader,
  CardBody,
  CardTitle,
  CardFooter,
} from "@progress/kendo-vue-layout";
// ES2015 module syntax
import { Input } from "@progress/kendo-vue-inputs";
import "@progress/kendo-theme-default";
import { Button } from "@progress/kendo-vue-buttons";

export default {
  name: "CardComponent",
  components: {
    card: Card,
    cardHeader: CardHeader,
    cardBody: CardBody,
    cardTitle: CardTitle,
    cardFooter: CardFooter,
    KInput: Input,
    kbutton: Button,
  },
  data() {
    return {
      lists: [
        { text: "Surface Laptop 2", checked: false },
        { text: "GooglePixel 4xl", checked: false },
        { text: "Sony 1000xm4", checked: false },
      ],
      currentList: "",
    };
  },
  methods: {
    addList() {
      this.lists.push({ text: this.currentList, checked: false });
      this.currentList = "";
    },
    removeList(index) {
      this.lists.splice(index, 1);
    },
  },
};
</script>
<style>
.list {
  width: 380px;
  /* border: 1px solid black; */
  display: flex;
  flex-direction: column;
  padding: 20px;
  /* background: #444444; */
}
li {
  list-style-type: none;
}
.form-box {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
  margin: 10px 0px;
}
.footer-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.card-container {
  background-color: #444444;
  color: white;
  border-radius: 0px;
}
.card-title {
  color: white;
}
.removed {
  color: #fca954;
}
.removed label {
  text-decoration: line-through;
}
</style>

