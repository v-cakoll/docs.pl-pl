---
title: Ładowanie elementu DataSet z pliku XML
description: Dowiedz się, jak dodać zawartość do zestawu danych ADO.NET z pliku XML. .NET Framework oferuje elastyczność do obciążenia i struktury zestawu danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 8c81e6e29678fe2e30af7c15d8d6e90f23dd0762
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286886"
---
# <a name="loading-a-dataset-from-xml"></a>Ładowanie elementu DataSet z pliku XML
Zawartość ADO.NET <xref:System.Data.DataSet> można utworzyć na podstawie strumienia lub dokumentu XML. Ponadto dzięki .NET Framework masz doskonałą elastyczność nad tym, jakie informacje są ładowane z pliku XML, oraz sposób tworzenia schematu lub struktury relacyjnej <xref:System.Data.DataSet> .  
  
 Aby wypełnić <xref:System.Data.DataSet> danymi z XML, użyj metody **ReadXml** <xref:System.Data.DataSet> obiektu. Metoda **ReadXml** odczytuje z pliku, strumienia lub elementu **XmlReader**i przyjmuje jako argumenty Źródło XML i opcjonalny argument **XmlReadMode** . Aby uzyskać więcej informacji na temat elementu **XmlReader**, zobacz [odczytywanie danych XML za pomocą XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). Metoda **ReadXml** odczytuje zawartość strumienia XML lub dokumentu i ładuje <xref:System.Data.DataSet> dane z danymi. Zostanie również utworzony schemat relacyjny w <xref:System.Data.DataSet> zależności od typu **XmlReadMode** oraz tego, czy schemat relacyjny już istnieje.  
  
 W poniższej tabeli opisano opcje dla argumentu **XmlReadMode** .  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Automatycznie**|Domyślnie włączone. Bada kod XML i wybiera najbardziej odpowiednią opcję w następującej kolejności:<br /><br /> -Jeśli plik XML jest w formacie DiffGram, jest używany element **DiffGram** .<br />-Jeśli <xref:System.Data.DataSet> zawiera schemat lub XML zawiera schemat wbudowany, **ReadSchema** jest używany.<br />-Jeśli nie <xref:System.Data.DataSet> zawiera schematu, a XML nie zawiera wbudowanego schematu, **InferSchema** jest używany.<br /><br /> Jeśli znasz format odczytywanego kodu XML, w celu uzyskania najlepszej wydajności zaleca się ustawienie jawnego elementu **XmlReadMode**, a nie akceptowanie **wartości domyślnej.**|  
|**ReadSchema**|Odczytuje wszystkie wbudowane schematy i ładuje dane i schemat.<br /><br /> Jeśli <xref:System.Data.DataSet> zawiera już schemat, nowe tabele są dodawane z schematu wbudowanego do istniejącego schematu w programie <xref:System.Data.DataSet> . Wyjątek jest zgłaszany, jeśli dowolna tabela w schemacie wbudowanym już istnieje <xref:System.Data.DataSet> . Nie będzie można modyfikować schematu istniejącej tabeli przy użyciu elementu **XmlReadMode. ReadSchema**.<br /><br /> Jeśli nie <xref:System.Data.DataSet> zawiera schematu i nie ma wbudowanego schematu, żadne dane nie są odczytywane.<br /><br /> Schemat wbudowany można zdefiniować przy użyciu schematu języka definicji schematu XML (XSD). Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje wszystkie wbudowane schemat i ładuje dane do istniejącego <xref:System.Data.DataSet> schematu. Wszystkie dane, które nie są zgodne z istniejącym schematem, są odrzucane. Jeśli żaden schemat nie istnieje w <xref:System.Data.DataSet> , żadne dane nie są ładowane.<br /><br /> Jeśli dane są w formacie DiffGram, **IgnoreSchema** ma takie same funkcje jak **DiffGram** *.*|  
|**InferSchema**|Ignoruje wszystkie wbudowane schemat i wnioskuje schemat na strukturę danych XML, a następnie ładuje dane.<br /><br /> Jeśli <xref:System.Data.DataSet> zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie kolumn do istniejących tabel. Dodatkowe tabele nie zostaną dodane, jeśli nie ma istniejących tabel. Wyjątek jest zgłaszany, jeśli wywnioskowana tabela już istnieje z inną przestrzenią nazw lub jeśli wszystkie wywnioskowane kolumny kolidują z istniejącymi kolumnami.<br /><br /> Aby uzyskać szczegółowe informacje na temat sposobu, w jaki program **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz [wnioskowanie o relacyjnej strukturze zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Formacie**|Odczytuje element DiffGram i dodaje dane do bieżącego schematu. Format **DiffGram** Scala nowe wiersze z istniejącymi wierszami, w których unikatowe wartości identyfikatorów są zgodne. Zobacz "scalanie danych z pliku XML" na końcu tego tematu. Aby uzyskać więcej informacji na temat DiffGrams, zobacz [DiffGrams](diffgrams.md).|  
|**Fragment**|Kontynuuje odczytywanie wielu fragmentów kodu XML do momentu osiągnięcia końca strumienia. Fragmenty, które pasują do <xref:System.Data.DataSet> schematu, są dołączane do odpowiednich tabel. Fragmenty, które nie pasują do <xref:System.Data.DataSet> schematu, są odrzucane.|  
  
> [!NOTE]
> Jeśli przekażesz element **XmlReader** do **ReadXml** , który jest umieszczony częścią sposobu w dokumencie XML, **ReadXml** zostanie odczytany do następnego węzła elementu i będzie traktowany jako element główny, odczytując do końca węzła elementu. Nie ma to zastosowania w przypadku określenia **XmlReadMode. fragment**.  
  
## <a name="dtd-entities"></a>Jednostki DTD  
 Jeśli plik XML zawiera jednostki zdefiniowane w schemacie definicji typu dokumentu (DTD), zostanie zgłoszony wyjątek w przypadku próby załadowania <xref:System.Data.DataSet> przez przekazanie pliku o nazwie, strumienia lub braku sprawdzania poprawności elementu **XmlReader** do **ReadXml**. Zamiast tego należy utworzyć element **XmlValidatingReader**z opcją **EntityHandling** ustawioną na **EntityHandling. ExpandEntities**i przekazać **XmlValidatingReader** do **ReadXml**. **XmlValidatingReader** rozwinie jednostki przed odczytaniem przez <xref:System.Data.DataSet> .  
  
 Poniższy przykład kodu przedstawia sposób ładowania <xref:System.Data.DataSet> ze strumienia XML. Pierwszy przykład przedstawia nazwę pliku, który jest przesyłany do metody **ReadXml** . W drugim przykładzie przedstawiono ciąg zawierający kod XML, który jest ładowany przy użyciu <xref:System.IO.StringReader> .  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> Jeśli wywołasz **ReadXml** do załadowania bardzo dużego pliku, może wystąpić spadek wydajności. Aby zapewnić najlepszą wydajność dla **ReadXml**, w dużym pliku Wywołaj <xref:System.Data.DataTable.BeginLoadData%2A> metodę dla każdej tabeli w <xref:System.Data.DataSet> , a następnie Wywołaj **ReadXml**. Na koniec Wywołaj <xref:System.Data.DataTable.EndLoadData%2A> dla każdej tabeli w <xref:System.Data.DataSet> , jak pokazano w poniższym przykładzie.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> Jeśli schemat XSD dla <xref:System.Data.DataSet> zawiera element **targetNamespace**, dane mogą nie być odczytywane i mogą wystąpić wyjątki, gdy wywołując **ReadXml** do ładowania <xref:System.Data.DataSet> pliku XML, który zawiera elementy bez kwalifikującej się przestrzeni nazw. Aby odczytywać niekwalifikowane elementy w tym przypadku, ustaw **elementFormDefault** równe "kwalifikowana" w schemacie XSD. Na przykład:  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Scalanie danych z pliku XML  
 Jeśli <xref:System.Data.DataSet> zawiera już dane, nowe dane z pliku XML zostaną dodane do danych znajdujących się już w <xref:System.Data.DataSet> . **ReadXml** nie scala danych z pliku XML z <xref:System.Data.DataSet> dowolnymi informacjami o wierszach ze zgodnymi kluczami podstawowymi. Aby zastąpić informacje o istniejących wierszach nowymi informacjami z pliku XML, użyj **ReadXml** , aby utworzyć nowe <xref:System.Data.DataSet> , a następnie <xref:System.Data.DataSet.Merge%2A> nowe <xref:System.Data.DataSet> do istniejącej <xref:System.Data.DataSet> . Należy zauważyć, że załadowanie pliku DiffGram przy użyciu **ReadXml** z atrybutem **XmlReadMode** z elementu **DiffGram** spowoduje scalenie wierszy, które mają ten sam unikatowy identyfikator.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DiffGram](diffgrams.md)
- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
