### <a name="xslt-forward-compat-now-works"></a>Działa teraz compat do przodu XSLT

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4 zgodność z nowszymi wersjami XSLT 1.0 ma następujące problemy:<ul><li>Ładowanie arkusza stylów kończyło się niepowodzeniem, jeśli jego wersja miała wartość 2.0, a analizator napotkał nierozpoznaną konstrukcję specyfikacji XSLT 1.0.</li><li><code>xsl:sort</code> Konstrukcja nie można sortować dane, jeśli wersja arkusza stylów została ustawiona w 1.1.</li></ul>W programie .NET Framework 4.5 zostały rozwiązać te problemy, a tryb zgodność z nowszymi wersjami XSLT 1.0 działa poprawnie.|
|Sugestia|Większość aplikacji powinna być wpływu, jednak dane będą sortowane inaczej w niektórych przypadkach skoro wzięty pod uwagę sort. Jeśli <code>xsl:sort</code> jest używany w 1.1 arkusze stylów, upewnij się, że aplikacje nie zostały w zależności od nieposortowane kolejność danych. Jeśli aplikacje zależne od 4.0 sortowanie zachowanie, Usuń <code>xsl:sort</code> z arkusza stylów.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|

