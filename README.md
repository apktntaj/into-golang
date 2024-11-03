# INTO GOLANG

Ini adalah catatan dalam proses belajar mendalami bahasa Golang.

## Hello World

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello World")
}
```

Go adalah bahasa yang dikompilasi ke bahasa mesin.

Function main adalah entri function dari program yang kita tulis.

Untuk menjalankan kode yang kita tulis kita bisa memasukkan command:

```bash
go run .
```

Untuk mengubah kode menjadi file executeable gunakan command:

```bash
go build .
```

lalu jalankan dengan command:

```bash
./<nama_project>
```

Kode sumber Go dibagi menjadi package. Program setidaknya harus memiliki satu package yaitu main dengan satu function main sebagai _identifier_.

Tiap file .go harus mendeklarasikan package, sebagai penanda file tersebut dimiliki oleh package apa. Biasanya, seluruh file dengan package yang sama dihimpun dalam satu folder dengan nama yang sama dengan nama package.

## Command Line Arguments

```go
// This program prints its command line arguments
package main

import (
	"fmt"
	"os"
)

func main() {
	var s, sep string
	for i := 1; i < len(os.Args); i++ {
		s += sep + os.Args[i]
		sep = " "
	}
	fmt.Println(s)
}

```

Package `os` adalah package yang menyediakan function yang berhubungan dengan sistem operasi.

Untuk manangkap argument kita bisa menggunakan `os.Args`.

os.Args adalah slice, struktur data yang banyak digunakan di bahasa Go.

Elemen pertama dari `os.Args` adalah nama dari program yang kita buat.

Seperti di banyak bahasa lain, `//` juga digunakan untuk membuat komentar.

By convention, setiap membuat package kita "wajib" membuat komentar sebagai deskripsi dari package tersebut.

Ketika mendeklarasikan variabel tanpa memasukkan nilai, Go akan otomatis menginisiasi value tersebut dengan "", 0, atau nil. Tergantung dari tipe datanya.

Go hanya memiliki satu bentuk perulangan.

```go
// Tradisional for loop.
for init; condition; post {
	// do what you wanna do
}

// Same like while loop.
for condition {
	// ...
}

// Infinite loop.
for {
	// ...
}
```

Go juga memiliki bentuk lain untuk melakukan perulangan dengan menggunakan _keyword_ `range`.

```go
for _, arg := range os.Args[1:] {
	fmt.Println(arg)
}
```

`range` menghasilkan sepasang value. Index dan value dari index tersebut. Pada contoh di atas kita tidak membutuhkan index. Itulah kenapa kita menggunakan _blank identifier_ `_`.

Blank identifier adalah cara untuk menampung variabel yang dihasilkan sebuah function yang tidak kita butuhkan dalam logic program.

<!-- ## Data agregat dari Goroutine

Konsep Goroutine dalam bahasa Go memang sangat berguna untuk menjalankan tugas secara konkuren. Namun, tanpa channel, goroutine sering kali menjadi sia-sia karena channel adalah salah satu cara utama untuk memungkinkan komunikasi dan sinkronisasi antar-goroutine.

```go
package main

import (
	"fmt"
	"time"
)

func GoRoutines() {
	start := time.Now()

	username := fetchUser()
	likes := fetchLikes()
	match := fetchMatch()

	fmt.Printf("%s Memiliki %d likes dan match dengan %s\n\n", username, likes, match)
	fmt.Println("Waktu fetch: ", time.Since(start))

}

func fetchUser() string {
	time.Sleep(time.Millisecond * 100)

	return "Bob"
}

func fetchLikes() int {
	time.Sleep(time.Millisecond * 150)

	return 11
}

func fetchMatch() string {
	time.Sleep(time.Millisecond * 100)

	return "Anna"
}

```

Pada kode di atas, kita menggunakan goroutine untuk -->
