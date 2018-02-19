Przygotowanie skryptu do uruchomienia produktu

1. Sprawdź stan\_produktu.sql
2. Uzupełnij plik ces\_id.txt \(uwaga! włącz opcję EOL Conversion -&gt; Unix w Notepad++\)
3. Uruchom ./prepare_activate_product.sh preprod , aby wygenerować skrypt na preproda
4. Uruchom na preprodzie ./activate\_product.sh

Jeżeli skrypt jest ok, to

1. Wrzuć skrypt do folderu z datą \production-deployment-scripts\deployments
2. skrypt na początku niech ma nazwę WARnnnn
3. commit, pull, push
4. Złóż SD na wdrożenie skryptu na produkcję



