## Pengenalan

### Membuat "Hello Vue"
```html
<div id="app">
  {{ message }}
</div>
```
```javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

### Kondisional dan perulangan sederhana
#### Kondisional
```html
<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>
```
```javascript
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```
terdapat atribut `v-if` yang memiliki nilai `"seen"`. Atribut tersebut akan memeriksa data dari `seen`, jika `seen == true` maka tulisan "Now you see me" akan terlihat.

#### Perulangan
```html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```
```javascript
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
```
Pada atribut `v-for="todo in todos` itu dapat diartikan ulangi yang berada pada data `todos` dengan variabel `todo`

### Binding sederhana
#### Menggunakan **button**
```html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>
```
```javascript
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```

#### Menguunakan input
```html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
```javascript
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```

### Membuat komponen sederhana
![components](https://vuejs.org/images/components.png)

Pembuatan komponen pada vue dilakukan saat pra definisi dengan format sebagai berikut:
```
// Pendefinisian komponen dengan nama todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})

var app = new Vue(...)
```

Dengan menggunakan komponen, kamu bisa langsung memanggil komponen tersebut sebagai tag
```html
<ol>
  <!-- Create an instance of the todo-item component -->
  <todo-item></todo-item>
</ol>
```

Pembuatan komponen yang membawa properti dapat dibuat sebagai berikut:
```javascript
Vue.component('todo-item', {
  // Komponen todo-item membawa properti todo
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
```

Penggunaan komponen yang membawa properti dapat dituliskan sebagai berikut:
```html
<div id="app-7">
  <ol>
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
```
```javascript
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
})
```
Pada atribut `v-for` mengikat variabel `groceryList` yang setiap perulangannya diletakan pada variabel `item`. Kemudian variabel `item` tersebut diikat pada properti `todo` menggunakan atribut `v-bind:todo="item"` dan juga properti `key` menggunakan atribut `v-bind:key="item.id"` (akan dijelaskan selanjutnya).

Dalam aplikasi skala besar, aplikasi tersebut dipecah menjadi beberapa komponen untuk mempbuat pengembangan menjadi lebih mudah untuk dikelola
```html
<div id="app">
  <app-nav></app-nav>
  <app-view>
    <app-sidebar></app-sidebar>
    <app-content></app-content>
  </app-view>
</div>
```

[Kembali](https://github.com/okyaneka/vue-tutorial/blob/master/README.md)
