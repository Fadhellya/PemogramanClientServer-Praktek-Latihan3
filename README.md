# PemogramanClientServer-Praktek
## Langkah - Langkah Membuat Latihan 3
### Langkah 1 : 
####  Buat proyek web menggunakan link berikut [start.spring.io](https://start.spring.io/)  kemudian pilih Spring web dan kemudian bahasa java dan sesuaikan versinya dengan device (disini saya menggunakan jdk 17  kemudian isi artifactnya(saya menggunakan latihan3-service) kemudian spring bootversinya pakai yang versi 2.6.11(yang saya pakai) dan untuk grubnya isi dengan com.fadhel kemudian download dan extrack dari zip menjadi file kemudian import ke dalam apache netbean 
### Langkah 2 :
#### buat sebuah class dengan nama Greeting.java dibawah package com.fadhel.latihan3.service kemudian isi dengan code berikut :
```java
package com.fadhel.latihan3.service;

public class Greeting {

	private final long id;
	private final String content;

	public Greeting(long id, String content) {
		this.id = id;
		this.content = content;
	}

	public long getId() {
		return id;
	}

	public String getContent() {
		return content;
	}
}
```
### Langkah 3 :
##### Kemudian cari proyek aplication.properties yang berada di Other Source >> src/main/resources >> <default package> >> aplication.properties kemudian masukkan code berikut :
```java
server.port=8012
```
### Langkah 4 :
##### buat sebuah class dengan nama GreetingController.java dibawah package com.fadhel.latihan3.service kemudian isi dengan code berikut :
```java
package com.fadhel.latihan3.service;
import java.util.concurrent.atomic.AtomicLong;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GreetingController {

	private static final String template = "Hello, %s!";
	private final AtomicLong counter = new AtomicLong();

	@GetMapping("/greeting")
	public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) {
		return new Greeting(counter.incrementAndGet(), String.format(template, name));
	}
}

```
### Langkah 5 :
##### setelah itu coba di buka link berikut [http://localhost:8012/greeting](http://localhost:8012/greeting)nanti akan muncul output seperti ini
```java
{"id":1,"content":"Hello, World!"}
```
### Langkah 6 :
##### setelah itu coba di buka link berikut [http://localhost:8012/greeting?name=User](http://localhost:8012/greeting?name=User) nanti akan muncul output seperti ini
```java
{"id":2,"content":"Hello, User!"}
```

