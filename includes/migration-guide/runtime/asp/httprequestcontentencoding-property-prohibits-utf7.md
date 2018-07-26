### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Właściwość HttpRequest.ContentEncoding zabrania UTF7

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=name>s' treści. Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.|
|Sugestia|W idealnym przypadku aplikacji powinien zostać zaktualizowany w taki sposób, aby nie używać kodowania w UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s. Alternatywnie, można przywrócić starsze zachowanie za pomocą <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) elementu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

