# Bekerja dengan String

## Rangkuman

* Walaupun string adalah tipe primitif di Javascript, tapi ada beberapa **properti** dan **method** yang bisa diterapkan.

* Properti `length` mengembalikan banyak karakter dalam string tersebut.

* String di Javascript bersifat  **[immutable]( https://en.wikipedia.org/wiki/Immutable_object )**: ketika dibuat, nilai string tidak akan berubah. Method dalam object string tidak akan pernah mengubah nilai awalnya namun akan selalu mengembalikan nilai baru.

* Method `toLowerCase()` dan `toUpperCase()` mengembalikan nilai baru string berupa huruf kecil dan huruf besar.

* String dapat dilihat sebagai array yang terdiri dari karakter. Dengan indeks pertama adalah 0.

* Anda bisa melakukan iterasi terhadap string dengan `for` atau `for-of`.

* Menggunakan method `Array.from()` Anda bisa mengubah string menjadi array yang terdiri atas karakter baru setelahnya anda dapat menggunakan `forEach()` untuk mengiterasikannya.

* Melakukan pencarian didalam string dapat menggunakan method `indexOf()`, `startsWith()` dan `endsWith()`.

* Method `split()` dapat digunakan untuk memecah string berdasarkan sebuah karakter pemisah. 

## Pengenalan String 

Mari ulas lagi apa yang telah dipelajari tentang String:

* Nilai string merepresentasikan teks.

* Di javascript, string didefinisikan dalam teks yang diapit oleh kutip satu (`'Saya string'`) atau kutip dua (`"Saya string"`).

* Karakter khusus dalam string diawali dengan (`\`) diikuti dengan karakter khusus tersebut. Contoh `\n` adalah karakter khusus untuk menambahkan baris baru.

* Operator tambah `+` digunakan untuk menggabungkan dua atau lebih string.

## Mendapatkan panjang string

Untuk mendapatkan panjang sebuah string, tinggal menambahkan `.length`. Panjang string akan dikembalikan dalam bentuk bilangan bulat.

```js
console.log("ABC".length); // 3
const str = "Saya string";
const len = str.length;
console.log(len); // 11
```

Walaupun string termasuk dalam tipedata primitif, beberapa properti dan method dapat diaplikasikan seperti halnya object, salah satunya adalah properti `.length`.

## Mengubah case string

Untuk mengubah string menjadi huruf kecil dapat digunakan method `toLowerCase()`, sedangkan `toUpperCase()` digunakan untuk mengubah jadi huruf besar.

```js
const kata = "Bora-bora";

const kataDalamHurufKecil = kata.toLowerCase();
console.log(kataDalamHurufKecil); // "bora-bora"

const kataDalamHurufBesar = kata.toUpperCase();
console.log(kataDalamHurufBesar); // "BORA-BORA"
```

`toLowerCase()` dan `toUpperCase()` adalah method string. Seperti setiap method keduanya tidak mengubah nilai awal dan akan mengembalikan nilai yang baru. 

T> Penting untuk diketahui bahwa ketika sebuah string dibuat nilainya tidak akan berubah. String dalam javascript adalah **immutable**.

## Membandingkan nilai string

Untuk membandingkan string dapat digunakan operator `===`. Operasi pembandingan akan mengembalikan nilai boolean `true` jika string sama dan `false` jika tidak sama.

```js
const kata = "koala";
console.log(kata === "koala"); // true
console.log(kata === "jerapah"); // false
```

W> Pembandingan string adalah case sensitive. Artinya nilai huruf kecil dan huruf besar dianggap berbeda.

```js
console.log("Qwerty" === "qwerty"); // false
console.log("Qwerty".toLowerCase() === "qwerty"); // true
```

## String adalah kumpulan beberapa karakter

### Mengidentifikasi sebuah karakter

Anda dapat membayangkan string sebagai sebuah array dari karakter. Setiap karakter dapat diakses melalui index, seperti halnya array, dengan ketentuan sebagai berikut.

* Index yang pertama adalah 0, bukan 1.
* Index karakter yang terakhir adalah panjang string - 1;

## Mengakses karakter dalam string

Untuk mengakses karakter dalam string dapat digunakan tanda kurung siku `[]` dengan index yang ditempatkan diantara keduanya.

W> Jika mencoba mengakses karakter yang diluar panjang string maka nilai `undefined` yang akan didapatkan.

```js
const olahraga = "bola basket";
console.log(olahraga[0]); // "o"
console.log(olahraga[6]); // "a"
console.log(olahraga[20]); // undefined: karakter terakhir berada pada index 10
```

## Perulangan pada string

Bagaimana jika Anda ingin mengakses semua karakter dalam string satu per satu ? Anda dapat mengakses masing-masing karakter seperti cara dibawah.

```js
const nama = "Sarah";
console.log(name[0]); // "S"
console.log(name[1]); // "a"
console.log(name[2]); // "r"
console.log(name[3]); // "a"
console.log(name[4]); // "h"
```

Namun cara diatas kurang praktis. Anda perlu solusi yang lebih baik dengan melakukan perulangan dalam mengakses masing-masing karakter. Konsep perulangan dapat kita terapkan untuk masalah ini.

Anda dapat menggunakan perulangan untuk mengakses masing-masing karakter dalam string. `for` adalah pilihan yang lebih baik dari `while`, karena kita sudah mengetahui berapa banyak karakter dalam string.

```js
for (let i = 0; i < sebuahString.length; i++) {
  // Gunakan sebuahString[i] untuk mengakses karakter dalam string satu per satu
}
```

Dalam perulangan diatas `i` adalah indikator yang menunjukan index karakter yang sedang diakses. Ketika nilai `i` bernilai sama dengan panjang string dikurangi 1 maka perulangan akan terhenti.

Kode dibawah akan menghasilkan output yang sama dengan contoh sebelumnya.

```js
const nama = "Sarah";
for (let i = 0; i < nama.length; i++) {
  console.log(nama[i]);
}
```

## Mengubah string menjadi array

Di javascript method `Array.from()` dapat digunakan untuk mengubah string menjadi array. Array tersebut kemudian dapat diproses lagi menggunakan method `forEach()`. Seperti contoh sebelumnya kode dibawah menampilkan karakter dari sebuah string satu per satu.

```js
const nama = "Sarah";
const namaArray = Array.from(nama);
namaArray.forEach(huruf => {
  console.log(huruf);
});
```

## Pencarian dalam string

Melakukan pencarian dalam sebuah string adalah hal yang lumrah.

Method `indexOf()` memerlukan sebuah parameter yang berisikan nilai yang dicari. Jika nilai tersebut ditemukan akan mengembalikan index pertama dimana nilai tersebut ditemukan, sebaliknya akan mengembalikan nilai -1 jika tidak ditemukan.

```js
const lagu = "Hongky Tonk Women";
console.log(song.indexOf("onk")); // 1
console.log(song.indexOf("Onk")); // -1 karena tidak ditemukan
```

Saat mencari nilai yang ada di awal atau akhir string dapat digunakan method `startsWith()` dan `endsWith()`. Kedua method tersebut mengembalikan nilai `true` atau `false`, tergantung dari nilai tersebut ditemukan atau tidak. Perlu diperhatikan method ini case sensitive.

```js
const song = "Honky Tonk Women";

console.log(song.startsWith("Honk")); // true
console.log(song.startsWith("honk")); // false
console.log(song.startsWith("Tonk")); // false

console.log(song.endsWith("men")); // true
console.log(song.endsWith("Men")); // false
console.log(song.endsWith("Tonk")); // false
```

## Memecah string

Kadang string terdiri dari beberapa bagian yangn dipisahkan oleh sebuah karakter tertentu. Pada kasus ini untuk mendapatkan masing-masing bagian dapat menggunakan method `split()`. Method ini mengambil parameter berupa karakter pemisah dan mengembalikan array yang terdiiri dari bagian-bagiannya.

```js
const semuaBulan = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";
const bulan = semuaBulan.split(",");
console.log(bulan[0]);  // "Jan"
console.log(bulan[11]); // "Dec"
```

## Waktunya Koding

### Info kata

Tulislah sebuah program yang meminta input kata dan menunjukan panjangnya, dalam huruf kecil dan besar.

### Palindrome

Tingkatkat program sebelumnya untuk melakukan pengecekan apakah kata tersebut palindrome atau bukan. Palindrome adalah kata yang jika dibalik akan tetap sama. Abaikan tanda, huruf kecil/besar dan spasi.

> Sebagai contoh `"radar"` adalah palindrome begitu juga dengan `"Radar"`
