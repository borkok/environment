# Custom Assertions

Po prostu wyraź to co chcesz by robiła asercja. Potem zapisz ją dokładnie w takiej formie. Na końcu zaimplementuj.

{% embed url="https://joel-costigliola.github.io/assertj/assertj-core-custom-assertions.html" %}

Jeżeli część kodu z asercjami rośnie, należy odłożyć na chwilę klawiaturę i zastanowić się jak powinna wyglądać sama asercja. Potem trzeba zastąpić cały kod tą właśnie jednoliniową asercją i postarać się ją zaimplementować korzystając z AssertJ czy Hamcresta.

Całkiem sensowne wydaje się też stworzenie własnych asercji dla najważniejszych obiektów domeny - istnieje spora szansa, że użyjesz ich zarówno w testach jednostkowych jak i integracyjnych.

Przykłady:

```text
TxDTOAssert
.assertThatFile("response.csv")
.hasTransaction("123cancel")
.withResultCode(SUCCESS); 
```

```text
SSHServerAssert.assertThat(ARTIFACT_FILE_NAME)
.existsOnServer(config)
.hasSize(WAR_FILE_LENGTH)
```

Spraw by testy i asercje mówiły w języku dziedziny problemu, a nie w języku szczegółów implementacyjnych.

Lepiej niż reużywana metoda prywatna - ta może się rozrosnąć do dużych rozmiarów z if'ami, aby móc ją reużyć w różnych przypadkach testowych.

Pozostaje pytanie, jak stworzyć wygodną w użyciu asercję? Ja po prostu piszę ją tak, żeby łatwo było ją przeczytać. Od tego zaczynam - pisze linijkę kodu, na przykład taką jak poniżej, nie przejmując się, że nie mam jeszcze implementacji: `assertThat(client).isVip().and().hasDiscount(0.2);` A potem biorę się do pisania implementacji. Oczywiście, czasami zdarza się, że muszę nieco zmienić asercję tak że powstały w wyniku DSL różni się nieco od tego wymarzonego. Trudno, czasami tak jest. Ale zazwyczaj udaje mi się zrobić dokładnie to co sobie zaplanowałem.

Czy pisać testy do własnych asercji?

_"Analizując dotychczasowe przykłady, w których zalecałem tworzenie własnych asercji, można zapytać o konieczność testowania ich. W końcu zdarzyć się może, że taka samodzielnie napisana asercja będzie zawierać jakąś logikę. Jak więc zyskać pewność, że nie kryje się w niej jakiś błąd? W tej kwestii mogę się przyznać: nie piszę testów do własnych asercji. Nigdy nie czułem takiej potrzeby. Wynika to z dwóch powodów._ 

_Po pierwsze, zazwyczaj we własnych asercjach nie pojawia się żadna logika. Ich działanie często sprowadza się do porównywania pól obiektów z oczekiwaniami. Pisząc własne asercje dla obiektów domeny raczej nie napotkasz potrzeby tworzenia żadnych pętli ani logiki w postaci wyrażeń warunkowych. Często zdarza się, że większość kodu dotyczy tworzenia bardzo czytelnych komunikatów o błędach. Czasami w testach integracyjnych, na przykład takich jak ten omawiany w sekcji 4.5.4, asercje są nieco bardziej skomplikowane. Jednak po przeniesieniu ich do własnej klasy zostają podzielone na mniejsze metody, co zazwyczaj eliminuje złożoność._ 

_Drugi powód jest innej natury. Otóż zazwyczaj własne asercje tworzę po tym, gdy już mam działający test z wieloma asercjami. W pewnym momencie po prostu przestaję być zadowolony z części "then" i wtedy zamieniam ją na własną asercję. Ta nowa klasa powstaje przez przenoszenie fragmentów kodu z oryginalnego testu. Poszczególne fragmenty trafiają do osobnych metod, i to w zasadzie tyle. Raczej trudno tu o błędy, a sytuację dodatkowo poprawia fakt, że nim przystąpię do przenoszenia kodu, mam już działający test. Gdy już przerobię go tak, by używał własnoręcznie stworzonej asercji, wystarczy go znów uruchomić by zobaczyć że wszystko nadal gra."_

