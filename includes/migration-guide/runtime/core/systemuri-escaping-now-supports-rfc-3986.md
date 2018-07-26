### <a name="systemuri-escaping-now-supports-rfc-3986"></a>Anulowanie System.Uri obsługuje teraz ze standardem RFC 3986

|   |   |
|---|---|
|Szczegóły|Identyfikator URI anulowania zapewnianego element został zmieniony w .NET Framework 4.5 do obsługi [ze standardem RFC 3986](http://tools.ietf.org/html/rfc3986). Określone zmiany obejmują:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> Wyprowadza zastrzeżone znaki oparte na dokumencie RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> nie wyprowadza zastrzeżonych znaków.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> nie zgłasza wyjątku, jeśli napotka nieprawidłową sekwencję ucieczki.</li><li>Niezastrzeżone znaki ucieczki przestają być znakami ucieczki.</li></ul>|
|Sugestia|<ul><li>Aktualizowanie aplikacji, aby nie zależą od <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> do zgłoszenia w przypadku nieprawidłową sekwencję ucieczki. Takie sekwencji muszą zostać wykryte bezpośrednio teraz.</li><li>Podobnie można oczekiwać, że ciągi Escaped i identyfikatora URI o niezmienionym znaczeniu i danych mogą się różnić od programu .NET Framework 4.0 i .NET Framework 4.5 i nie powinny być porównywane w wersjach .NET bezpośrednio. Zamiast tego powinien być analizowane i znormalizowane w jednej wersji .NET, zanim wszystkie porównania są wykonywane.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

