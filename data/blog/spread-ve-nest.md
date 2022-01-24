---
title: JavaScript'de Spread ve Rext
date: '2022-01-24'
tags: ['javascript', 'js']
draft: false
summary: JavaScript'de üç nokta olarak kullanılan spread ve rest ne işe yarar?
---

JavaScript'e yeni başlayanlar üç nokta şeklinde kullanılan ifadesini görmüştür. Peki nedir bu spread ve rest?

## Ne işe yarar?

İngilizcede yaymak anlamına gelen spread JavaScript içerisinde de aynı işlevi yapar. Başına koyduğumuz objelerin veya dizilerin her bir elemanını yayar.

```javascript
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// output: 6
console.log(sum(numbers[0], numbers[1], numbers[2]))
// output: 6
```

Örnekte sayıları toplamak için bir fonksiyon ve çalışması için 3 tane değerimiz var.
numbers dizisindeki değerleri toplamak istediğimde bu verileri tek tek yazmak yerine spread ifadesini kullanarak sayılarıı yayabiliriz.

## Function kullanımı

```javascript
myFunction(...myArray)
```
Fonksiyonlarda değer vermek için kullanabiliriz.
Verilen örnekte tüm dizi elemanlarını fonsiyona göndermiş olduk.

## Array kullanımı

```javascript
let array = [1,2,3]
let newArray = [...array, 4, 5]

let fruits = ["apple", "orange", "banana"]
let newFruits = ["kiwi", ...fruits, "melon"]
console.log(newFruits)
// ["kiwi", "apple", "orange", "banana", "melon"]
```
Dizileri bu şekilde başka dizilere aktarmak için kullanabiliriz.

## Object kullanımı

JavaScript'de bir objeyi diğer objeye eşitlersek herhangi birinde yaptığımız değişiklik diğerine de uygulanır.

```javascript

let object = { name: "Muharrem", surname: "Dursun", age: 17 }
let newObject = object;
newObject["age"] = 18;
console.log(object)
//{ name: "Muharrem", surname: "Dursun", age: 18 }

```

`newObject` içerisindeki değeri değiştirmemize rağmen `object` içerisindeki değerimiz de değişti.
Obje içerisindeki değerleri diğerine aktarmak için aşağıdaki yöntemi kullanmak gerekir.

```javascript

let object = { name: "Muharrem", surname: "Dursun", age: 17 }
let newObject = {...object};
newObject["age"] = 18;
console.log(object)
// { name: "Muharrem", surname: "Dursun", age: 17 }
console.log(newObject)
// { name: "Muharrem", surname: "Dursun", age: 18 }
```

Bu örnekte ise iki obje birbirinden bağımsız.

## Fonsiyonlar için varsayılan değer oluşturma

```javascript 
function myFunction(value, value2, settings){
let defaultSettings = {
something: true,
another: false
}
settings = {
...defaultSettings,
...settings
}
//your code
}
let options = {
something: false
}
myFunction(1, 2, options)
```

Bu örnekte `options`da `another` değerini belirtmedik. Fakat spread ifadesi sayesinde varsayılan bir değer atamış olduk.
Fonsiyon içerisinde `options` değerini yazdırırsak bunun uygulandığını görmüş oluruz.
