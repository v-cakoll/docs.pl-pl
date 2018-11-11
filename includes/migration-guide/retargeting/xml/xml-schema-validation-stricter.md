### <a name="xml-schema-validation-is-stricter"></a>Walidacja schematu XML jest bardziej rygorystyczna

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 walidacja schematu XML jest bardziej rygorystyczna. Jeśli element xsd:anyURI zostanie użyty w celu walidacji identyfikatora URI, takiego jak protokół mailto, walidacja nie powiedzie się, jeśli w identyfikatorze URI znajdują się spacje. W poprzednich wersjach programu .NET Framework walidacja kończyła się pomyślnie. Ta zmiana dotyczy tylko aplikacji, których platformą docelową jest program .NET Framework 4.5.|
|Sugestia|W razie potrzeby użycia mniej rygorystycznej walidacji (stosowanej w programie .NET Framework 4.0) można określić program .NET Framework 4.0 jako platformę docelową aplikacji używanej do walidacji. Jednak w przypadku przekierowania do programu .NET Framework 4.5 należy wykonać przegląd kodu, aby upewnić się, że nieprawidłowe identyfikatory URI (ze spacjami) nie są oczekiwane jako wartości atrybutu z typem danych anyURI.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|

