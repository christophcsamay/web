<!DOCTYPE html>
<html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todooey - A Simple Todo List App</title>
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <style>
      html,
body {
  margin: 0;
  padding: 0;
  background: #faffff;
  font-size: 16px;
}

* {
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  color: #3d4855;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin-top: 0;
}

.container {
  padding: 24px 0;
  max-width: 700px;
  width: 100%;
  margin: 0 auto;
}

.card {
  border-radius: 4px;
  box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
  background: white;
  margin-bottom: 24px;
}

.card-inner {
  padding: 16px 24px;
}

.flex {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input {
  border-radius: 4px;
  background: transparent;
  border: none;
  width: 100%;
  padding: 14px;
  font-size: 16px;
  border: 1px solid transparent;
  height: 100%;
  display: block;
  outline: none;
}

button {
  background: #4fc08d;
  padding: 10px 22px;
  border: none;
  color: white;
  border-radius: 4px;
  margin: 8px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 1px 1px 15px -2px #212c4430;
  transition: 0.15s;
}

button:hover {
  background: #42aa7b;
}

button:disabled {
  background: #e8e8e8;
  color: #555;
  box-shadow: none;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.list-item {
  padding: 12px 16px 12px 16px;
  border: 1px solid #e8e8e8;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-bottom: 6px;
  border-radius: 4px;
}

.list-item:first-child {
  border-top: 1px solid #e8e8e8;
}

.list-item-toggle {
  border: 1px solid #e8e8e8;
  border-radius: 999px;
  height: 21px;
  width: 21px;
  margin-right: 16px;
}

.list-item-delete {
  margin-left: auto;
  color: tomato;
  margin-top: -2px;
  font-weight: bold;
  text-decoration: none !important;
}

.list-item.completed {
  border: 1px solid #4fc08d;
}

.list-item.completed span {
  text-decoration: line-through;
}

.list-item.completed .list-item-toggle {
  background: #4fc08d;
  border: #4fc08d;
}
    </style>

  </head>

  <body>
    <div class="container">
      <div id="app">
        <h1 class="">My Todo List</h1>
        <div class="card">
          <div class="flex">
            <input v-model="newItem" @keyup.enter="addItem" placeholder="Add new todo" />
            <button @click="addItem" :disabled="newItem.length === 0">Add</button>
          </div>
        </div>
        <div class="card">
          <div class="card-inner">
            <h2>Todo</h2>
            <ul class="list">
              <li class="list-item" :class="{completed: item.completed}" v-for="item in reversedItems">
                <div class="list-item-toggle" @click="toggleCompleted(item)"></div><span>{{ item.name }}</span>
                <div class="list-item-delete" @click="removeItem(item)">X</div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <script>    const shoppingList = new Vue({
      el: '#vue',
      data: {
        newItem: '',
        items: [
          {
            id: 1,
            name: 'Clean the fridge',
            completed: false,
          },
          {
            id: 2,
            name: 'Walk the dogs',
            completed: true,
          },
        ],
      },
      computed: {
        reversedItems() {
          return this.items.slice(0).reverse();
        },
      },
      methods: {
        addItem: function () {
          this.items.push({
            id: this.items.length + 1,
            name: this.newItem,
            completed: false,
          });
          this.newItem = '';
        },
        toggleCompleted: function (item) {
          item.completed = !item.completed;
        },
        removeItem: function (item) {
          this.items = this.items.filter((newItem) => newItem.name !== item.name);
        },
      },
    });</script>
    <script>
      new Vue( {
        el: '#app',
        data: {
          newItem: '',
          items: [
            {
              id: 1,
              name: 'Clean the fridge',
              completed: false,
            },
            {
              id: 2,
              name: 'Walk the dogs',
              completed: true,
            },
          ],
        },
        computed: {
          reversedItems() {
            return this.items.slice( 0 ).reverse();
          },
        },
        methods: {
          addItem: function () {
            this.items.push( {
              id: this.items.length + 1,
              name: this.newItem,
              completed: false,
            } );
            this.newItem = '';
          },
          toggleCompleted: function ( item ) {
            item.completed = !item.completed;
          },
          removeItem: function ( item ) {
            this.items = this.items.filter( ( newItem ) => newItem.name !== item.name );
          },
        },
      } );
      app.mount('#app')
    </script>


  </body>

</html>