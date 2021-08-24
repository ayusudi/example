<img src="./assets/4.png" style="height:120px;object-fit:contains">

# Lecture AM 
- [Instance Method](#instance-method)
- [Static Method](#static-method)
- [Seqeulize Hooks](#hooks)

Telah tersedia aplikasi dengan fitur Create, Read, Delete & <a href="https://sequelize.org/master/class/lib/model.js~Model.html#static-method-increment"> Increment </a> Point terhadap User

Lecture kita kali ini ada 3 materi dengan 2 diantara sudah kalian kenal sebelumnya di week 1.   

<br>

## Instance Method

Instance method, method dijalankan oleh instance dan method ini dapat mengakses this, seperti pada umumnya kita buat pada class di model. 

~~Jalankan nodemon ke aplikasi ⤵️~~

![image](./assets/1.png)

Kita ingin user memiliki nama dengan panggilan Tuan / Nyonya tanpa mengubah data dalam table.

![image](./assets/2.png)


## Static Method 

Tahukah kalian bahwa selama ini kalian menggunakan static method di sequelize?  
tapi semua itu adalah static method yang telah sediakan sequelize seperti built-in function.  

```txt
Model.namaMethod()

ex : 
User.create()
```

Pada **case** kali ini kita akan buat versi kita sendiri, misalnya kita ingin membuat feature yang bernama `Increment Random 0 - 9`.  
Feature ini akan menggantikan feature increment yang telah ada.


## Hooks 

Hooks, hooks adalah sebuah proses yang **terkait** pada eksekusi event(dapat sebelum atau setelah) disebut juga sebagai lifecyle.  
Hooks bisa saja terdapat di framework lain dengan cara yang berbeda.

Mungkin saat ini urutan fitur create yang telah kalian kenal adalah 

> Input data -> Validasi -> Data ditambahkan ke database -> Kembali ke halaman utama

Tapi itu bukan hooks, itu merupakan flow atau algorithma dari fitur create.

---


### [Sequelize Hooks (click here)](http://sequelize.org/master/manual/hooks.html)  
sebuah proses yang terjadi sebelum dan setalah eksekusi method sequlize (create, update, destroy, etc). 

buka slide H8 untuk menjelaskan sedikit keamanan data password

![image](./assets/3.png)

Apabila hooks tidak di declare maka dia tidak ada

#### CASE
~~Jalankan nodemon ke aplikasi~~  

User dengan bebas membuat nama mereka dengan bebagai format namun pada database kita harus terformat dengan proper
```txt
Example : 
Input dari user  "ayu SUDI dwijayanti" 

Nama yang disimpan pada database "Ayu Sudi Dwijayanti"
```

Untuk hooks method Delete (destroy) dan Update menggunakan <a href="https://sequelize.org/master/manual/hooks.html#:~:text=can%20pass%20the%20%7B-,individualHooks,-%3A%20true%20%7D%20option%20to">individualHooks</a> pada options
```txt
User.update(value, options)
User.destroy(options)
```