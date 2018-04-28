### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception — prawidłowo teraz Ustawia pozycje wiersza

|   |   |
|---|---|
|Szczegóły|Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przekazywany do metody obciążenia i wystąpi błąd sprawdzania poprawności, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości zawierają teraz informacje dotyczące wiersza.|
|Sugestia|Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie będzie zestaw powinien zostać zaktualizowany, ponieważ te właściwości będą teraz można ustawić poprawnie, gdy SetLineInfo jest używany podczas ładowania danych XML.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

