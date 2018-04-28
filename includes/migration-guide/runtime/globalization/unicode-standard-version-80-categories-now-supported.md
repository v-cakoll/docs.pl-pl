### <a name="unicode-standard-version-80-categories-now-supported"></a>Standardowa wersji 8.0 kodowania Unicode z kategorii teraz obsługiwane

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 danych Unicode w ramach został uaktualniony z wersji standard 6.3 Unicode do wersji 8.0.  Podczas żądania Kategoria znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.  Ta zmiana przede wszystkim ma wpływ sylab Cherokee i nowe znaki samogłoski Tai artość i znaczniki sygnału.|
|Sugestia|Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalony kategorie znaków Unicode.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

