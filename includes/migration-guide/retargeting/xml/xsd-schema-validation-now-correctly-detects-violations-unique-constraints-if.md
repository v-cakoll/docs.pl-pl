### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Weryfikacja schematu XSD teraz prawidłowo wykrywane naruszenia ograniczenia unique klucze złożone są używane, jeśli jeden klucz jest pusty

|   |   |
|---|---|
|Szczegóły|Wersje programu .NET Framework, przed 4.6 miał usterkę, która spowodowała Weryfikacja schematu XSD nie wykryć ograniczenia unikatowy kluczy złożonych, gdy jeden z kluczy jest pusta. W .NET Framework 4.6 ten problem został rozwiązany. Spowoduje to bardziej poprawne sprawdzania poprawności, ale również może spowodować niektórych XML nie weryfikacji, który wcześniej musi.|
|Sugestia|W razie potrzeby im weryfikacji programu .NET Framework 4.0 sprawdzania poprawności aplikacji celem może być w wersji 4.5 (lub starszym) programu .NET Framework. Podczas przekierowania 4.6 .NET, jednak przeglądu kodu ma się odbywać należy upewnić się, że zduplikowane klucze złożone (zgodnie z opisem w opisie tego problemu) nie powinny do sprawdzania poprawności.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowania|

