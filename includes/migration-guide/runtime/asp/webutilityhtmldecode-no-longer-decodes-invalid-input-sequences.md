### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode dekoduje nie jest już nieprawidłowy sekwencji wejściowych

|   |   |
|---|---|
|Szczegóły|Domyślnie metody dekodowania nie dekodują już nieprawidłowych sekwencji wejściowych na nieprawidłowy ciąg UTF-16. Zamiast tego zwracają oryginalne dane wejściowe.|
|Sugestia|Zmiana w danych wyjściowych dekodera powinna mieć znaczenie tylko wtedy, gdy w ciągach zamiast danych UTF-16 są przechowywane dane binarne. Aby jawnie kontroli tego zachowania, należy ustawić <code>aspnet:AllowRelaxedUnicodeDecoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu <code>true</code> umożliwia zachowanie starszej wersji lub do <code>false</code> umożliwia zachowanie bieżącego.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|

