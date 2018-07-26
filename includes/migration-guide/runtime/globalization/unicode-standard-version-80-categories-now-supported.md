### <a name="unicode-standard-version-80-categories-now-supported"></a>Teraz obsługiwane kategorie standardowej wersji 8.0 Unicode

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 danych Unicode został uaktualniony ze standardu Unicode wersji 6.3 do wersji 8.0.  Podczas żądania kategorii znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.  Ta zmiana przede wszystkim ma wpływ sylab Czirokeski i nowe Tai artość samogłosek znaki i znaki tonowe.|
|Sugestia|Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalonych kategorii znaków Unicode.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

