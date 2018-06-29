### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() i FormattedText.Extent zwracać różne wartości, w programie .NET Framework 4.5

|   |   |
|---|---|
|Szczegóły|Wprowadzono ulepszenia <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> i <xref:System.Windows.Media.FormattedText.Extent> w programie .NET Framework 4.5 do rozwiązywania problemów, gdy pola zostały za mała dla wartości zawartych w niej symboli w niektórych przypadkach w .NET Framework 4.0. W wyniku tego niektóre obwiedni będzie większy począwszy od wersji programu .NET Framework 4.5, co powoduje niewielkie różnice w układzie interfejsu użytkownika.|
|Sugestia|Należy pamiętać, że niektóre rozmiarach pól ograniczający symbolu nastąpiło nasilenie. Te zmiany zwykle poprawi prezentacji i testowania trafień pola, ale w razie potrzeby starsze zachowanie (wstępne .NET 4.5) może być do wybrał, dodając następujący wpis do pliku app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

