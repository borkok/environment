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

* zamiast rozbudowanej sekcji then można **napisać własną klasę asercji** - więcej patrz podstrona [custom-assertions](https://app.gitbook.com/@kinga/s/environment/~/drafts/-M49q-PPwmdobowCfUWM/zle-testy-dobre-testy/custom-assertions)

* By sprawdzić czy test jest zgodny z zasadą SRP można zadać następujące pytanie;

  "Gdy ten test nie przejdzie, to czy patrząc na nazwę jego metody będę w stanie

  określić jaka funkcjonalność mojej aplikacji nie działa?".

* Logika w testach to zło! Nawet najprostsza!

* Testuj odpowiedzialności, a nie metody. Prosta reguła: "Jedna metoda robi kilka rzeczy? Potrzebujesz kilku testów!".

  * Główna różnica pomiędzy pierwotną wersją a tą zaproponowaną przeze mnie polega na tym, że pierwotna wersja testowała metodę registerUser\(\) podczas gdy aktualna wersja skupia się na testowaniu odpowiedzialności klasy UserRegisterController. W aktualnej wersji każda z metod testowych skupia się na weryfikacji jednej odpowiedzialności klasy. Skoro jedną z odpowiedzialności klasy jest przekierowanie użytkownika po prawidłowym wypełnieniu formularza, to mamy test, który to sprawdza. Innym wymaganiem jest by klasa wysłała powiadomienie po udanej rejestracji. I na to również mamy osobny test.

* Mockować vs tworzyć prawdziwe obiekty
  * Główną zaletą zastosowania mocka nad użyciem new District\(\) jest to, że mocka nie obchodzi to jak konstruuje się obiekty tej klasy. Ta cecha mocka może okazać się całkiem wartościowa, zwłaszcza w obliczu \(prawdopoobnej\) ewolucji klasy District. Być może już w tej chwili jej konstruktor przyjmuje kilka argumentów. Być może w przyszłości te argumenty "urosną" - zwiększy się ich liczba, lub być może proste typy zostaną zastąpione przez typy złożone
* given/when/then jest ok, ale nie na siłę zawsze - przy małych testach 2-3 linijkowych testach nie ma sensu

* jak tworzyć obiekty w testach - **test data builder** [test-data-builder](https://app.gitbook.com/@kinga/s/environment/zle-testy-dobre-testy/test-data-builder)

* nadawaj staranne nazwy zmiennym, np. zamiast user1, user2, user3 =&gt; userWith1PLEntry, userWith4PLEntries. Łatwo o pomyłkę gdy nazwy zmiennych różnią się tylko nieznacznie. Nie używaj sufiksów ani prefixów do odróżniania poszczególnych zmiennych w testach! Tak dobierz nazwy obiektów, by jasno określały ich specyfikę
* Myśląc o nazwie metody testowej zostawmy w spokoju implementację. Liczą się wymagania. Autor zaleca nazywanie metod od should

* Unikaj porównywania do oczekiwanego obiektu `assertThat(result).isEqualTo(expectedResult);`
  * Porównywanie obiektów sprawia, że warstwa biznesowa testu staje się mniej czytelna, a na pierwszy plan wysuwają się szczegóły techniczne. Historia opowiadana przez test zanika: końcówka testu mówi tylko, że jakieś dwa obiekty powinny być identyczne. Raczej sugerowałbym napisanie kilku asercji \(lub stworzenie jednej własne\), co pozwoli na lepsze wyrażenie intencji testu.
  * Jeżeli klasa DataModel nie posiada rozsądnej implementacji metody toString\(\), wówczas jeżeli test nie przejdzie, dowiemy się raczej niewiele. Być może zobaczymy taki oto komunikat: org.junit.ComparisonFailure: Expected :my.company.DataModel@e6037658 Actual :my.company.DataModel@4af66537
  * Innym problemem jest to, że taki test porównujący całe obiekty może nie przejść z powodu różnicy w zawartości obiektów zupełnie nieistotnej w kontekście rozpatrywanego scenariusza.

