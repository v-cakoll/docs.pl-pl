### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Metoda System.Uri.IsWellFormedUriString zwraca wartość false dla względne identyfikatory URI przy użyciu znaku dwukropek w pierwszy segment

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traktują względne identyfikatory URI z <code>:</code> w ich pierwszy segment, ponieważ niepoprawnie sformułowany. To różni się od <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> zachowania w programie .NET Framework 4.0 do RFC3986 została wprowadzona w celu.|
|Sugestia|Ta zmiana (na przykład wiele innych zmian URI) mają wpływ tylko na aplikacje zgodne z .NET Framework 4.5 (lub nowszy). Aby nadal używać starego zachowania, aplikacja jest przeznaczona dla .NET Framework 4.0. Alternatywnie skanowania identyfikatory URI przed wywołaniem <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> szukasz <code>:</code> znaki, które warto usunąć do celów sprawdzania poprawności, jeśli pożądane jest stare zachowanie.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

