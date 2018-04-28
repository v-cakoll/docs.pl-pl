### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Metoda System.Uri.IsWellFormedUriString zwraca wartość false dla względne identyfikatory URI zawierające wartość typu char dwukropka w segmencie pierwszy

|   |   |
|---|---|
|Szczegóły|Począwszy od platformy .NET Framework 4.5 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traktują względne identyfikatory URI ze <code>:</code> w ich pierwszy segment, ponieważ niepoprawnie sformułowany. Jest to zmiana z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> zachowanie w .NET Framework 4.0 RFC3986 wprowadzone są zgodne.|
|Sugestia|Ta zmiana (na przykład wiele innych zmian identyfikatora URI) mają wpływ tylko na aplikacje docelowy program .NET Framework 4.5 (lub nowszej). Aby nadal używać starego zachowania, docelowe aplikacji .NET Framework 4.0. Alternatywnie skanowania identyfikatorów URI przed wywołaniem <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> wyszukiwanie <code>:</code> znaki, które może chcesz usunąć do celów sprawdzania poprawności, jeśli poprzednie działanie jest pożądane.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

