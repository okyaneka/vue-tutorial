## Sintaks template

### Interpolasi

#### Teks

Menggunakan kurung kurawal

```html
<span>Message: {{ msg }}</span>
```

Ditampilkan sekali
```html
<span v-once>This will never change: {{ msg }}</span>
```

#### Raw HTML

Menggunakan atribut `v-html`

```javascript
...
  data: {
    rawHtml: '<span style="color: red">This should be red.</span>'
  }
...
```
```html
<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```




[Kembali](https://github.com/okyaneka/vue-tutorial/blob/master/README.md)
