### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Zwraca ciąg nieco inny, ContentDisposition Data/Godzina

|   |   |
|---|---|
|Szczegóły|Reprezentacji ciągów obiektu <xref:System.Net.Mime.ContentDisposition?displayProperty=name>firmy zostały zaktualizowane, począwszy od 4.6, aby zawsze reprezentuje składnik godziny z <xref:System.DateTime?displayProperty=name> z dwoma cyframi. Pozwala to wykonania [RFC822](http://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Powoduje to, że <xref:System.Net.Mime.ContentDisposition.ToString> zwraca ciąg nieco inne w wersji 4.6 w scenariuszach, w których jeden z elementów czasu dyspozycji zakończyła się przed 10:00:00. Należy pamiętać, że ContentDispositions czasami są serializowane przez konwertowanie ich na ciągi znaków, więc wszelkie <xref:System.Net.Mime.ContentDisposition.ToString> operacji, serializacji lub wywołania metody GetHashCode powinny być zweryfikowane pod.|
|Sugestia|Nie oczekuje, że ciągów reprezentujących ContentDispositions z różnych wersji programu .NET Framework poprawnie zostanie porównany ze sobą. Konwertowanie ciągów do ContentDispositions, jeśli to możliwe, przed przeprowadzeniem porównanie.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

