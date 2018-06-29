### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teraz specjalne spacje w ciągach przekazano za pomocą parametrów trasy

|   |   |
|---|---|
|Szczegóły|Aby można było zgodne z RFC 2396, spacji w ścieżkach trasy są teraz wyjściowym podczas wypełniania parametry akcji z trasy. Tak podczas gdy <code>/controller/action/some data</code> wcześniej spowoduje dopasowanie trasy <code>/controller/action/{data}</code> i podaj <code>some data</code> jako parametr danych teraz będzie ona <code>some%20data</code> zamiast tego.|
|Sugestia|Kod powinien zostać zaktualizowany do unescape parametrów ciągu z trasy. W razie potrzeby oryginalnego identyfikatora URI jest dostępny z <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString interfejsu API.|
|Zakres|Pomocnicza|
|Wersja|4.5.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

