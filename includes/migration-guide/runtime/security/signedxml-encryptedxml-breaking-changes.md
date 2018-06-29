### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml i EncryptedXml fundamentalne zmiany

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2, poprawki zabezpieczeń z <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> i <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> prowadzić do różne zachowania czasu wykonywania. Na przykład<ul><li>Jeśli dokument ma wiele elementów o takiej samej <code>id</code> atrybut i podpis przeznaczony dla jednego z tych elementów jako główny podpisu, dokumentu będą teraz uznawane za nieprawidłowe.</li><li>Dokumentów za pomocą-canonical algorytmów przekształcenia XPath w odwołaniach teraz są uznawane za nieprawidłowe.</li><li>Dokumentów za pomocą-canonical algorytmów przekształcenia XSLT w odwołaniach są teraz należy wziąć pod uwagę nieprawidłowy.</li><li>W tym celu nie będzie żadnych program korzystające z zasobu zewnętrznego odłączyć podpisów.</li></ul>|
|Sugestia|Deweloperzy mogą chcieć Sprawdź użycie elementu <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> i <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, a także typy pochodzące z <xref:System.Security.Cryptography.Xml.Transform> od odbiornika dokumentu nie można go przetworzyć.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|

