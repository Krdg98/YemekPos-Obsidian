[[Customer Rest API]] gelen isteklerin içeriye alınamdan önce gelen verileri doğru formatta oluduğunu kontrol eder.

İlk önce Microsoft'un kontrolünü daha sonra [[Fluent Validation]] kontrolünü yapar.

[[ModelState]] (DataAnnotations) hatası varsa **ValidationFilter** girebilmesi için ilgili Rest API nin **Program.cc** aşağıdaki kod eklenmelidir. Aksi taktirde  [[ModelState]] hatası oluşursa **ValidationFiler** girmez.

```
builder.Services.Configure<ApiBehaviorOptions>(options =>
{
    options.SuppressModelStateInvalidFilter = true;
});
```