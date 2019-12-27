## Contoh Vue

### Pembuatan VUE

```javascript
var vm = new Vue({
  // options
})
```

### Data dan methods

```javascript
// Data yang kita buat
var data = { a: 1 }

// Data ditambahkan ke contoh vue
var vm = new Vue({
  data: data
})

// Mendapatkan data dari vue
// mengembalikannya dengan variabel data yang telah dibuat sebelumnya
vm.a == data.a // => true

// Data pada vue dapat diedit
// Berefek pada variabel data yang telah dibuat sebelumnya
vm.a = 2
data.a // => 2

// ... begitupun sebaliknya
data.a = 3
vm.a // => 3
```

Data tersebut bersifat **reaktiv**, artinya adalah ketika data tersebut berubah, maka vue akan merender ulang. Perlu diperhatikan, data tersebut akan bersifat reaktif jika telah didefinisikan pada vue. Artinya adalah ketika vue ditambahkan data baru:

```javascript
vm.h1 = 'h1'
```

dan menudian mengubah data `h1` maka tidak akan menimbulkan perubahan tampilan.

### Lifecycle diagram

![Lifecycle diagram](https://vuejs.org/images/lifecycle.png)

[Kembali](https://github.com/okyaneka/vue-tutorial/blob/master/README.md)
