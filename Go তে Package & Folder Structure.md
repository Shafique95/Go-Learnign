
# Go তে Package & Folder Structure: সহজ ও মজাদার ব্যাখ্যা (বাংলায়)

আপনি যদি Go (গোল্যাং) শেখার শুরুতে থাকেন, তাহলে অবশ্যই `package` এবং ফোল্ডার স্ট্রাকচারের ব্যাপারে একটু মাথা ঘামিয়েছেন। আমি আজ খুব সহজ ভাষায় বাংলা কালচার দিয়ে আপনাদের জন্য এই জিনিসগুলো বুঝিয়ে দিবো — যাতে Go শেখা মজা হয়! 🎉

---

## Package কি?

`package` হচ্ছে কোডের **একটি ঘর বা বিভাগ**। যেমন, আপনার বাড়িতে আলাদা আলাদা রুম আছে — রান্নাঘর, ঘুমঘর, বাথরুম। Go তে আমরা কোডকে ছোট ছোট প্যাকেজে ভাগ করি যাতে পরিষ্কার এবং ব্যবস্থাপনা সহজ হয়।

---

## নিয়ম ১: এক ফোল্ডারে সব ফাইলের package নাম এক হতে হবে!

একটা ফোল্ডারে যদি ৫টা Go ফাইল থাকে, তাদের সব ফাইলের প্রথম লাইনে থাকা `package` এর নাম একই হবে।

**ভুল:**

```
same_folder/
 ├── file1.go (package foo)
 └── file2.go (package bar)  ← error হবে
```

**সঠিক:**

```
same_folder/
 ├── file1.go (package same_folder)
 └── file2.go (package same_folder)
```

---

## নিয়ম ২: আলাদা আলাদা package চাইলে আলাদা আলাদা ফোল্ডার করবেন

যেমন:

```
project/
├── post/         (package post)
│   ├── handler.go
│   ├── model.go
│   └── service.go
├── user/         (package user)
│   ├── handler.go
│   ├── model.go
│   └── service.go
└── main.go       (package main)
```

`main.go` ফাইল থেকে আপনি এইসব প্যাকেজ ইমপোর্ট করে কাজ করবেন।

---

## বাস্তব উদাহরণ: আমার গ্রাম 🌾 (একটি মজার Go প্রোগ্রাম)

আমাদের গ্রামে তিনজন:

* দাদা (দাদার কথা)
* আম্মা (রান্না করে)
* ভাই (বাবাজি করে)

প্রত্যেকের কথা আলাদা প্যাকেজে লিখবো। `main.go` থেকে ডাকে।

### dada/kata.go

```go
package dada

import "fmt"

func DadarKotha() {
    fmt.Println("👴 দাদা: বেটা, সময় নষ্ট করিস না... Go শিখ।")
}
```

### amma/ranna.go

```go
package amma

import "fmt"

func RannaBana() {
    fmt.Println("👩‍🍳 আম্মা: ভাত হয়ে গেছে, এখন Go code কর।")
}
```

### bhai/ulta.go

```go
package bhai

import "fmt"

func UltaPaltaKotha() {
    fmt.Println("😈 ভাই: ভাইয়া, Go শেখো না... PUBG খেলি?")
}
```

### main.go

```go
package main

import (
    "fmt"

    "amar-gram/dada"
    "amar-gram/amma"
    "amar-gram/bhai"
)

func main() {
    fmt.Println("🏠 গ্রামের বাড়িতে এক সকাল...")

    dada.DadarKotha()
    amma.RannaBana()
    bhai.UltaPaltaKotha()

    fmt.Println("🚀 শেষ পর্যন্ত সবাই Go শেখার কথাই বলল!")
}
```

---

## রান করার নিয়ম

```bash
mkdir amar-gram && cd amar-gram
go mod init amar-gram
mkdir dada amma bhai
# প্রতিটি ফাইলে কোড কপি করুন
go run main.go
```

---

## Output

```
🏠 গ্রামের বাড়িতে এক সকাল...
👴 দাদা: বেটা, সময় নষ্ট করিস না... Go শিখ।
👩‍🍳 আম্মা: ভাত হয়ে গেছে, এখন Go code কর।
😈 ভাই: ভাইয়া, Go শেখো না... PUBG খেলি?
🚀 শেষ পর্যন্ত সবাই Go শেখার কথাই বলল!
```

---

## শেষ কথা

Go তে **package = কোডের ঘর**।
এক ফোল্ডারে একটাই প্যাকেজ থাকতে হবে।
বিভিন্ন package হলে আলাদা ফোল্ডারে রাখবেন।
এটা কোডকে পরিষ্কার, সহজে মেইনটেইনযোগ্য এবং স্কেলেবল করে তোলে।

শেখা শুরু করুন ছোট থেকে, ধীরে ধীরে বড় প্রজেক্ট বানান।
Go শেখা হলে আপনার ক্যারিয়ার অনেকদূর যাবে!

