### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode i BMP obustronne WebUtility.HtmlDecode poprawnie

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla środowiska .NET Framework 4.5, znaki, które są poza Basic Multilingual Plane (BMP), wykonują rundę poprawnie, gdy są przekazywane do <xref:System.Net.WebUtility.HtmlDecode(System.String)> metody.|
|Sugestia|Ta zmiana powinny mieć żadnego wpływu na bieżące aplikacje, ale aby przywrócić oryginalne zachowanie, ustaw <code>targetFramework</code> atrybutu <code>&lt;httpRuntime&gt;</code> element na ciąg znaków innych niż &quot;4.5&quot;. Można również ustawić <code>unicodeEncodingConformance</code> i <code>unicodeDecodingConformance</code> atrybuty <code>&lt;webUtility&gt;</code> element konfiguracji do sterowania tym zachowaniem niezależnie od wersji docelowej programu .NET Framework.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|

