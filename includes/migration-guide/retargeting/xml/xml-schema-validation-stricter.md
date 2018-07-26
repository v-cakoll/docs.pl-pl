### <a name="xml-schema-validation-is-stricter"></a>Sprawdzanie poprawności schematu XML jest bardziej restrykcyjny

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5 sprawdzanie poprawności schematu XML jest bardziej rygorystyczna. Jeśli element xsd:anyURI zostanie użyty w celu walidacji identyfikatora URI, takiego jak protokół mailto, walidacja nie powiedzie się, jeśli w identyfikatorze URI znajdują się spacje. W poprzednich wersjach programu .NET Framework walidacja kończyła się pomyślnie. Zmiana dotyczy tylko aplikacji, których platformą docelową .NET Framework 4.5.|
|Sugestia|W razie potrzeby im weryfikacji programu .NET Framework 4.0 weryfikowania aplikacji mogą określać docelową systemu .NET Framework w wersji 4.0. W przypadku przekierowania do .NET Framework 4.5, jednak przeglądu kodu powinna być podejmowana należy upewnić się, że nieprawidłowe identyfikatory URI (ze spacjami) nie powinny jako wartości atrybutu z typem danych anyURI.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|

