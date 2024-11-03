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

## Data agregat dari Goroutine

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

Pada kode di atas, kita menggunakan goroutine untuk