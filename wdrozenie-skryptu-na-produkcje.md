Przygotowanie skryptu do uruchomienia produktu

1. Sprawdź stan\_produktu.sql
2. Uzupełnij plik ces\_id.txt \(uwaga! włącz opcję EOL Conversion -&gt; Unix w Notepad++\)
3. Uruchom ./prepare\_activate\_product.sh preprod , aby wygenerować skrypt na preproda
4. Uruchom na preprodzie ./activate\_product.sh

Jeżeli skrypt jest ok, to

1. Wrzuć skrypt do folderu z datą \production-deployment-scripts\deployments
2. skrypt na początku niech ma nazwę WARnnnn
3. commit, pull, push
4. Złóż SD na wdrożenie skryptu na produkcję

Skrypty z INSERTami powinny być wykonywane w okienku serwisowym.

1. Sigma utrzymuje bufor wygenerowanych w przód identyfikatorów.
2. Wdrożenie skryptu w ciągu dnia może spowodować, że SQL Server przydzieli dla rekordu identyfikator taki sam, jak zarezerwowany przez Sigmę
3. ```
   @SequenceGenerator
   (name = "sqIdClientOperationStackEntry", sequenceName = "sqClientOperationStackEntry", allocationSize = 100)
   ```

Odblokowanie i standardowe UNDO-REDO

1. Zobacz rozwiązanie dla WAR-4750 wraz ze zgłoszonym SD. Są tam dołączone skrypty weryfikacyjne dla undo-redo.
2. Do blokowanie stosu i odblokowania jest przygotowany skrypt generujący skrypty.
3. Zawsze sprawdź najpierw czy nie chodzi EOD

-- czy chodzi EOD?

SELECT \* FROM \[Configuration\].\[dbo\].SystemParam sp where sp.symbol = 'EOD\_PROCESSING';   
select \* from Core..EodExecution order by id desc 



