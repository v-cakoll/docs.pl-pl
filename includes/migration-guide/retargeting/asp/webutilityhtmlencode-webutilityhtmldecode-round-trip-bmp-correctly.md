### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode i BMP obustronne WebUtility.HtmlDecode poprawnie

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla platformy .NET Framework 4.5, znaki, które są poza wyrównana podstawowe płaszczyzny wielojęzyczne (BMP) poprawnie, gdy są one przekazywane do <xref:System.Net.WebUtility.HtmlDecode(System.String)> metody.|
|Sugestia|Ta zmiana powinna nie mają wpływu na bieżące aplikacje, ale aby przywrócić oryginalne zachowanie, ustaw <code>targetFramework</code> atrybutu <code>&lt;httpRuntime&gt;</code> elementu innego niż ciąg &quot;4.5&quot;. Można również ustawić <code>unicodeEncodingConformance</code> i <code>unicodeDecodingConformance</code> atrybuty <code>&lt;webUtility&gt;</code> element konfiguracji do kontrolowania tego zachowania, niezależnie od docelowa wersja programu .NET Framework.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|

