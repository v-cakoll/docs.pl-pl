### <a name="xml-schema-validation-is-stricter"></a>Sprawdzanie poprawności schematu XML jest bardziej restrykcyjne

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 sprawdzanie poprawności schematu XML jest ściślejsze. Jeśli element xsd:anyURI zostanie użyty w celu walidacji identyfikatora URI, takiego jak protokół mailto, walidacja nie powiedzie się, jeśli w identyfikatorze URI znajdują się spacje. W poprzednich wersjach programu .NET Framework walidacja kończyła się pomyślnie. Dotyczy tylko aplikacji przeznaczonych .NET Framework 4.5.|
|Sugestia|W razie potrzeby im weryfikacji programu .NET Framework 4.0 sprawdzania poprawności aplikacji można kierować programu .NET Framework w wersji 4.0. W przypadku przekierowania do programu .NET Framework 4.5, jednak przeglądu kodu ma się odbywać należy upewnić się, że nieprawidłowe identyfikatory URI (ze spacjami) nie powinny jako wartości atrybutu z typem danych anyURI.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|

