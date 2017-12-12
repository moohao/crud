<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="newDate" @keyup.enter="addNewItem">
    <ul>
      <li v-for="(item, index) in items">
        {{ index }}:
        <span v-on:click="changeStatus(item)" v-show="!item.editable">{{ item.data }}</span><input @keyup.enter="changeStatus(item)" v-show="item.editable" type="text" v-model="item.data"> <span class="delete" v-on:click="deleteItem(index)">X</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      msg: 'Welcome',
      items: [],
      newDate: ''
    }
  },
  methods: {
    addNewItem: function () {
      this.items.push({data: this.newDate, editable: false})
      this.newDate = ''
    },
    deleteItem: function (index) {
      this.items.splice(index, 1)
    },
    changeStatus: function (item) {
      item.editable = !item.editable
    }
  }
}
</script>

<style scoped>
.hello {
  text-align: center;
}
li{list-style: none;}
.delete {
  color: red;
}
</style>
