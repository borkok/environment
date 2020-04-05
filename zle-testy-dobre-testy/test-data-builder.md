---
description: Tworzenie obiektów testowych
---

# Test Data Builder

Unikasz dodawania do kodu prod. konstruktorów/setterów wykorzystywanych specjalnie dla testów

Tylko jedna klasa \(budowniczy\) wie jak stworzyć obiekt określonej klasy, więc zmiany będą dotyczyć tylko tej jednej klasy,

Builder niech ma znaczące metody, np. `UserBuilder.createActiveUser() .withCompany(company) .create();`

Budowniczy obiektów testowych to wyspecjalizowana klasa odpowiedzialna za tworzenie obiektów określonego typu na potrzeby testów. Sens ich istnienia jest następujący: 

* sprawiają, że testy nie wiedzą nic o konstruowaniu obiektów, których używają,
* niwelują potrzebę zaśmiecania kodu produkcyjnego dodatkowymi konstruktorami i metodami tworzonymi wyłącznie na potrzeby testów,
* standaryzują sposób tworzenia obiektów w kodzie testowym,
* dostarczają wygodnych metod, dzięki którym tworzenie obiektów jest bardzo proste \(i przyjemne do czytania\).
* `User user = new UserBuilder().standardUser() .but().withEmail("elvis@presley.com")` 
* `.and().withPassword("sivle")` 
* `.create();`

* w przypadku obiektów, które mają kilka pól z datami, opłaca się udostępnić metody przyjmujące tekstowe ich reprezentacje \(np. "2015-08-15"\) zamiast konstruować obiekty typu Date.
* tak samo lepiej przekazywać liczby całkowite niż BigDecimal.

