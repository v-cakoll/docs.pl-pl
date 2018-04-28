### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT styl arkusza komunikat o wyjątku zmienione

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 jest tekst komunikatu o błędzie podczas plik XSLT jest zbyt złożony &quot;arkusza stylów jest zbyt złożony.&quot; W poprzednich wersjach, komunikat o błędzie był &quot;błąd kompilacji XSLT.&quot; Kod aplikacji, który zależy od tekstu komunikatu o błędzie, przestanie działać. Jednak typów wyjątków pozostają takie same, ta zmiana powinna nie wpływają prawdziwe.|
|Sugestia|Każdy kod aplikacji, w zależności od komunikat wyjątku z tego błędu można spodziewać się nowy komunikat zaktualizować lub (lepszy) kod, aby tylko zależą od typu wyjątku (<xref:System.Xml.Xsl.XsltException?displayProperty=name>), który nie został zmieniony.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

