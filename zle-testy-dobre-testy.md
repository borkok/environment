---
description: >-
  Notatki z książki dostępnej do pobrania tutaj:
  https://leanpub.com/zletestydobretesty
---

# Złe testy, dobre testy



* Mockito: isA\(...class\) zamiast any\(...class\), bo any\(\) nie sprawdza typu argumentu

* zawsze powinniśmy raczej weryfikować wynik

  działania, a nie sposób w jaki został on uzyskany.  dlatego staraj się nie sprawdzać, czy wywołano metodę \(verify\), ale rezultat \(assertThat\) \(np. wartość pola obiektu się zmieniła\)

* Nie rób założeń co do zawartości bazy danych. Używaj raczej wartości względnych niż absolutnych \(np, że liczba rekordów będzie = 1, a nie zwiększyła się o 1\)

* Nigdy nie używaj System.currentTimeMillis\(\) albo new Date\(\) w kodzie

  produkcyjnym. Stwórz dodatkową warstwę abstrakcji - np. interfejs TimeProvider - którego domyślna implementacja zwróci aktualny czas. To pozwoli wygodnie testować funkcjonalności uzależnione od czasu.

* "partial mocking" \(użycie metody Mockito.spy\(\) na prawdziwym obiekcie\),

  co jest sygnałem ostrzegawczym i powinno budzić podejrzenia.

* Pisz testy jednostkowe dla fragmentów kodu, które wykazują przynajmniej

  minimalny stopień komplikacji. Nie marnuj czasu na testowanie tego, co złamać się nie może. \(gettery, settery, delegatory - np. 

  * public BigDecimal getImportantValue\(\) {

    return settings.getImportantValue\(\);

    }\)

* jedna z zasad dobrego mockowania: "mockuj tylko własne typy"

* Pisanie testu nie polega na odwzorowywaniu kodu produkcyjnego linia po linii!

  * "Zbyt szczegółowe testy są często źródłem wszelkiego zła. Popełnione w nich błędy skutkują opłakanymi w skutkach i długotrwałymi konsekwencjami. Nim się tego nauczyłem przez blisko dwa lata tworzyłem zbyt szczegółowe testy pewnego frameworku, aż w końcu okazało się, że kompletnie uniemożliwiają one jakikolwiek refaktoring. "
  * Nigdy, przenigdy nie weryfikuj algorytmu metody krok po kroku! Weryfikuj wynik algorytmu! Powinieneś mieć swobodę zmiany implementacji metody, tak długo jak wynik – to czego naprawdę oczekujesz – nie ulegnie zmianie.

* Przerośnięte testy

  * Zamiast jednego testu z rozbudowaną sekcją then zastanów się, czy możesz wydzielić osobne wymagania biznesowe. Rozdzielenie wymagań między trzy testy zapewnia nam dobry feedback.
  * Uwaga na kopiuj-wklej W przypadku testów metoda kopiuj i wklej prowadzi do: • przerośniętych części tworzących obiekty - kopiowanie prowadzi do tworzenia obiektów z wypełnionymi polami zupełnie nieistotnymi w danym scenariuszu testowym, • zbyt wielu asercji weryfikujących kwestie niezwiązane z danym przypadkiem testowym.

* verifyNoMoreInteractions\(\) powinna

  być używana z rozwagą. Jak zaznaczono w dokumentacji Mockito: "Używać

  tylko gdy w razie konieczności. Nadużywanie prowadzi do tworzenia testów

  zbyt szczegółowych i trudniejszych w utrzymaniu."

* zamiast rozbudowanej sekcji then można napisać własną klasę asercji TxDTOAssert.assertThatFile\("response.csv"\)

  .hasTransaction\("123cancel"\).withResultCode\(SUCCESS\); [https://joel-costigliola.github.io/assertj/assertj-core-custom-assertions.html](https://joel-costigliola.github.io/assertj/assertj-core-custom-assertions.html)

* By sprawdzić czy test jest zgodny z zasadą SRP można zadać następujące pytanie;

  "Gdy ten test nie przejdzie, to czy patrząc na nazwę jego metody będę w stanie

  określić jaka funkcjonalność mojej aplikacji nie działa?".

