# javascript-string-methods-all
Bu belge javascript string tiplerinin temel metotlarını içeren Türkçe belge niteliğinde hazırlanmış notlardan oluşur. Metotlar, tanımları ve kullanım örneklerinden oluşur. Hazırlayan @burakkrt 

# String Methods

### String.fromCharCode()

Belirtilen ASCII (UTF-16) kodun string karşılığı verir.

```jsx
console.log(String.fromCharCode(246,199)); //return "öÇ"
```

### String.raw()

**`\n`**, **`\t`**, **`\\`** gibi kaçış ifadeleri (boşluk bırakma, alt satıra geçme..vb) string değerin işlevini gerçekleştirmeden sadece string değer olarak kalmasını sağlar.

```jsx
console.log(`hello\njavascript`)
// "hello
// javascript"

console.log(String.raw`hello\njavascript`)
// "hello javascript"
```

### length()

String ifadenin toplam karakter sayısını verir. UTF-16 ya göre karakterleri sayar.,

```jsx
const myString = "bluebells";
console.log(myString.length) //return 9

myString.length = 4;  //Hiçbir etki sağlamaz. Değer ve uzunluk aynıdır.
```

### concat()

İki veya daha fazla string ifadeyi birleştirerek geriye döndürür.

```jsx
const str1 = 'Hello';
const str2 = 'World';
console.log(str1.concat(" ", str2); //return "Hello World"

const arr = ["Merhaba","!","Sisteme"," ","Hoşgeldiniz"];
console.log("Burak".concat(...arr)) //return "Burak Merhaba!Sisteme Hoşgeldiniz."

const arr2 = [1,2,3,4];
console.log("".concat(...arr2)) /return "1234";
```

### endsWith()

String bir ifadenin belirli bir karakter ile bitip bitmediğini denetler ve geriye `true` veya `false` döndürür.

```jsx
const str1 = 'Cats are the best!';
console.log(str1.endsWith('best!')); //return true 

const str2 = "Hello World";
console.log(str2.endsWith("llo",5)) //return true
//(value,endPosition)
// 5.indexdeki değerden balaşlayıp geriye doğru(4. 3. index) "llo" değerini ara.
```

### includes()

String ifadenin içerisinde belirtilen değerin varlığını sorgular ve geriye `true` veya `false` değer döndürür.

```jsx
const sentence = 'The quick brown fox jumps over the lazy dog.';
const searchChars = "FoX"

console.log(`Bu cümlede ${searchChars} kelimesi ${sentence.toLowerCase().includes(searchChars.toLowerCase()) ? "geçiyor." : "geçmiyor."}`)
// return "Bu cümlede FoX kelimesi geçiyor"
```

### indexOf()

String değerin içerisinde belirtilen kelime bulunuyor ise index numarasını geriye döndürür. Yok ise `-1` değerini döndürür.

```jsx
const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

console.log(paragraph.indexOf('quick')); //return 4 (4. indexten sonra bu kelime var)
console.log(paragraph.indexOf('test')); //return -1 (yok)
```

### **localeCompare()**

İki dizeyi belli bir yerel dil ve düzenlemeye göre karşılaştırarak sonuçlarını döndürür. Dize karşılaştırması yapılırken, metin sıralaması, harf büyüklüğü, aksanlar ve diğer dil özellikleri dikkate alınır. Bu nedenle, dil ve yerelleştirme kurallarına göre doğru dize sıralamasını elde etmek için tercih edilir. Bu sayede, farklı dillerdeki karakterleri ve özel işaretleme ve aksanları içeren dize sıralamaları düzgün bir şekilde yapılabilir.

`localeCompare(compareString, locales, options)`

1. Eğer **`dize`**, **`karsilastirilacakDize`**'den daha küçükse, `-1` döner.
2. Eğer **`dize`** ve **`karsilastirilacakDize`** birbirine eşitse, **`0`** döner.
3. Eğer **`dize`**, **`karsilastirilacakDize`**'den daha büyükse, **`1`** döner.

**sensitivity**

Karşılaştırma sırasında büyük/küçük harf ve diğer duyarlılıkları belirler.

|  | accent | case | base | variant |
| --- | --- | --- | --- | --- |
| Büyük / Küçük Harf Duyarlılığı | Hayır | Evet | Hayır | Evet |
| Aksan duyarlılığı | Evet | Hayır | Hayır | Evet |

```jsx
console.log("apple".localeCompare("banana")); //return -1 (dize1 , dize2 den küçük)
console.log("apple".localeCompare("apple")); //return 0 (eşit)

console.log("Café".localeCompare("Café", undefined, {sensitivity : "variant"}))
	//return -1 Eşit(Hem aksan hemde büyük küçük harf eşit olmalı)
console.log("cafe".localeCompare("Café", undefined, {sensitivity : "base"}));
	//return 0 Eşit(Sadece string.length() eşit olsa yeterli.)
console.log("Cafe".localeCompare("Café", undefined, {sensitivity : "case"}));
	//return 0 Eşit(sadece büyük küçük harf duyarlılığı)
console.log("cafe".localeCompare("Café", undefined, {sensitivity : "accent"}));
	//return 0 Eşit(sadece aksan duyarlığı)

```

### padStart()

Bir string değerin başına belirli bir uzunluğa kadar tekrar ederek ilgili değer ile doldurur.

```jsx
let str = "45"

console.log(str.padStart(5,"1")) // "11145"

const cardNumber = "2034399002125581";
const private = cardNumber.slice(-4).padStart(cardNumber.length,"*")
console.log(private); // "************5581"
```

### padEnd()

Bir string değerin sonuna belirli bir uzunluğa kadar tekrar ederek ilgili değer ile doldurur.

```jsx
let str = "Hello World"

console.log(str.padEnd(14,".")) // "Hello World..."
console.log(str.padEnd(str.length + 3, "!")) // "Hello World!!!"
console.log("abc".padEnd(10)); // "abc       "
console.log("abc".padEnd(6, "123456")); // "abc123"
```

### repead()

İlgili string değeri belirtilen sayı kadar tekrar eden yeni bir string döndürür.

```jsx
const cardNumber = "123";

console.log(cardNumber.repeat(2)); // "123123"
```

### replace()

İlgili string ifadenin içerisinde belirtilen değeri bir başka değer ile değiştirip, değiştirilmiş ifadeyi geriye döndürür. İlk bulduğu değeri dönüştürür, birden fazla aynı değere etki etmez.

```jsx
const str = "Ali ata bak";
const str = "Ali ata bak ata";

console.log(str.replace("ata","arabaya")) // "Ali arabaya bak"
console.log(str.replace("ata","arabaya")) // "Ali arabaya bak ata"
```

### replaceAll()

İlgili stringin içerisinde belirtilen değeri bir başka değer ile değiştirip, değiştirilmiş ifadeyi geriye döndürür. Eğer birden fazla aynı ifade var ise hepsinde değişiklik uygular.

```jsx
const str = "Ali ata bak ata";

console.log(str.replaceAll("ata","arabaya")) // "Ali arabaya bak arabaya"
```

### slice()

İlgili string ‘de belirtilen indexlerdeki ifadeleri çıkartıp geriye döndürür. Orijinal ifadeyi değiştirmez, sadece belirtilen bölümünü kopyalayıp geriye döndürür.

```jsx
const str = 'The quick brown fox jumps over the lazy dog.';

console.log(str.slice(31));
// Expected output: "the lazy dog."

console.log(str.slice(4, 19));
// Expected output: "quick brown fox"

console.log(str.slice(-4));
// Expected output: "dog."

console.log(str.slice(-9, -5));
// Expected output: "lazy"
```

### split()

İlgili string ifadede belirtilen değeri arar ve bu değerden itibaren parçalara ayırıp bir dizi olarak geriye döndürür.

```jsx
const str = "Ali ata bak atın rengi kırmızı"

console.log(str.split("ata")); //["Ali "," bak atın rengi kırmızı"]
console.log(str.split("ata")); //["Ali","ata","bak","atın","rengi","kırmızı"]
console.log(str.split(" ",3)); //["Ali","ata","bak"] (en fazla 3 değer döndür)
```

### startWith()

İlgili string ‘in belirtilen ifade ile başlayıp başlamadığını kontrol eder ve boolean değer döndürür.

```jsx
const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));// true
console.log(str1.startsWith('Sat', 3));// false (3. indexten itibaren kontrol et)
console.log(str1.startsWith('urd', 3));// true
```

### substring()

İlgili string ‘de başlangıç ve bitiş indexine göre değeri döndürür.

```jsx
const str = 'Mozilla';

console.log(str.substring(1, 3));// "oz"
console.log(str.substring(2));// "zilla" (bitiş index değeri yoksa sonuna kadar keser)
console.log(str.substring(2,1));// "oz" (sondan başa doğru da aynı değer alınabilir)
```

### toLocaleLowerCase() , toLocaleUpperCase()

Dizenin tüm karakterlerini yerel dil kurallarına uygun olarak küçük harflere dönüştürür.

```jsx
console.log("DUBAI GÜZEL".toLocaleLowerCase("tr"));// dubaı güzel
//Türkçeye göre çevirdiği için ve türkçede küçük ı bulunduğundan I harfini ı ya çevirir

console.log("DUBAI GÜZEL".toLocaleLowerCase("en-US"));// dubai güzel
//İngilizcede büyük ı küçük i ye tekabül ettiği için i olarak çevrildi.
```

### toString()

Bir nesneyi veya veri türünü uygun bir string temsiline dönüştürür.

```jsx
const nbr = 42;
console.log(nbr.toString()); // "42"

const array = [1, 2, 3];
console.log(array.toString()); // "1,2,3"

const boolValue = true;
const strBool = boolValue.toString(); // "true"

const obj = { name: "John", age: 30 };
console.log(obj.toString()); // çevrilmez
```

### trim()

İlgili string ‘in **başında** ve **sonunda** bulunan “ “ (boşluk) ları temizleyerek yeni bir string döndürür.

```jsx
const str = "   ali mali    "
console.log(str.trim()); // "ali mali"
```

### trimStart()

İlgili string ‘in **başında** bulunan “ “ (boşluk) ları temizleyerek yeni bir string döndürür.

```jsx
const str = "   ali mali    "
console.log(str.trim()); // "ali mali    "
```

### trimEnd()

İlgili string ‘in **sonunda** bulunan “ “ (boşluk) ları temizleyerek yeni bir string döndürür.

```jsx
const str = "   ali mali    "
console.log(str.trim()); // "   ali mali"
```

### charAt()

İlgili string ‘de belirtilen index ‘de ki karakteri geriye döndürür.

```jsx
const str = "Ali ata bak"
console.log(str.charAt(2)); //return "i"
```
