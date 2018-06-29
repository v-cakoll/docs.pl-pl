### <a name="systemuri-escaping-now-supports-rfc-3986"></a>Anulowanie System.Uri obsługuje teraz RFC 3986

|   |   |
|---|---|
|Szczegóły|Anulowanie identyfikatora URI został zmieniony w programie .NET Framework 4.5 do obsługi [RFC 3986](http://tools.ietf.org/html/rfc3986). Określone zmiany obejmują:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> Wyprowadza zastrzeżone znaki oparte na RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> nie Usuń zastrzeżone znaki.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> nie Zgłoś wyjątek, jeśli wykryje nieprawidłową sekwencję ucieczki.</li><li>Niezastrzeżone znaki ucieczki przestają być znakami ucieczki.</li></ul>|
|Sugestia|<ul><li>Aktualizowanie aplikacji nie polegać na <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> ma zostać zgłoszony w przypadku nieprawidłową sekwencję ucieczki. Takie sekwencje muszą zostać wykryte bezpośrednio teraz.</li><li>Podobnie oczekują, że ciągów Escaped i URI niezmienionym znaczeniu oraz dane mogą się różnić od programu .NET Framework 4.0 i .NET Framework 4.5 i nie powinny być porównywane przez wersje .NET bezpośrednio. Zamiast tego należy można analizować i znormalizowany w jednej wersji platformy .NET, zanim wszystkie porównań.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

