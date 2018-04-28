### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Nieco inny ciąg zwraca ContentDisposition dat i godzin

|   |   |
|---|---|
|Szczegóły|Reprezentacja ciągu <xref:System.Net.Mime.ContentDisposition?displayProperty=name>firmy zostały zaktualizowane, począwszy od 4.6, aby zawsze reprezentuje składnik godziny z <xref:System.DateTime?displayProperty=name> z dwóch cyfr. Jest to w celu zapewnienia przestrzegania [RFC822](http://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Powoduje to <xref:System.Net.Mime.ContentDisposition.ToString> zwraca ciąg nieco inne w wersji 4.6 w scenariuszach, w którym został jeden z elementów czasu dyspozycji przed 10:00 AM. Należy pamiętać, że ContentDispositions czasami są serializowane za pośrednictwem ich konwertowanie na ciągi, tak aby <xref:System.Net.Mime.ContentDisposition.ToString> należałoby operacji, serializacji lub wywołania metody GetHashCode.|
|Sugestia|Nie oczekuje, że poprawnie porównuje reprezentacji ciągu ContentDispositions z różnych wersji .NET Framework ze sobą. Konwertowanie ciągów do ContentDispositions, jeśli to możliwe, przed przeprowadzeniem porównania.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

