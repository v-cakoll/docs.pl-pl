### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT stylu arkusz komunikat o wyjątku zmienione

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5 jest tekst komunikatu o błędzie, gdy plik XSLT jest zbyt złożony &quot;arkusz stylów jest zbyt złożony.&quot; W poprzednich wersjach komunikat o błędzie &quot;chyba kompilace XSLT.&quot; Kod aplikacji, który zależy od tekstu komunikatu o błędzie, przestanie działać. Typy wyjątków pozostają jednak takie same, więc ta zmiana nie powinna mieć rzeczywistego wpływu.|
|Sugestia|Aktualizację wszelkiego kodu aplikacji, w zależności od komunikat o wyjątku z ten warunek wystąpienia błędu można oczekiwać, Nowa wiadomość lub (jeszcze lepsze) zaktualizować kod, aby być zależne tylko od typu wyjątku (<xref:System.Xml.Xsl.XsltException?displayProperty=name>), który nie został zmieniony.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

