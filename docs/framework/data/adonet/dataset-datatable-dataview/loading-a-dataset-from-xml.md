---
title: Ładowanie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151068"
---
# <a name="loading-a-dataset-from-xml"></a>Ładowanie elementu DataSet z pliku XML
Zawartość ADO.NET <xref:System.Data.DataSet> można utworzyć na podstawie strumienia lub dokumentu XML. Ponadto w ramach .NET Framework masz dużą elastyczność w odniesieniu do informacji, które są ładowane z XML i jak tworzony <xref:System.Data.DataSet> jest schemat lub relacyjne struktury.  
  
 Aby wypełnić dane <xref:System.Data.DataSet> z XML, użyj metody <xref:System.Data.DataSet> **ReadXml** obiektu. Metoda **ReadXml** odczytuje z pliku, strumienia lub **XmlReader**i przyjmuje jako argumenty źródło XML oraz opcjonalny argument **XmlReadMode.** Aby uzyskać więcej informacji na temat **czytnika XmlReader,** zobacz [Odczytywanie danych XML za pomocą czytnika XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). Metoda **ReadXml** odczytuje zawartość strumienia lub dokumentu XML i ładuje <xref:System.Data.DataSet> dane. Spowoduje to również utworzenie schematu <xref:System.Data.DataSet> relacyjnego w zależności od **XmlReadMode** określony i czy schemat relacyjne już istnieje.  
  
 W poniższej tabeli opisano opcje argumentu **XmlReadMode.**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Automatycznie**|Domyślnie włączone. Sprawdza kod XML i wybiera najbardziej odpowiednią opcję w następującej kolejności:<br /><br /> - Jeśli XML jest DiffGram, **DiffGram** jest używany.<br />- Jeśli <xref:System.Data.DataSet> zawiera schemat lub XML zawiera wbudowany schemat, **ReadSchema** jest używany.<br />- Jeśli <xref:System.Data.DataSet> nie zawiera schematu i XML nie zawiera schematu wbudowanego, **InferSchema** jest używany.<br /><br /> Jeśli znasz format odczytu pliku XML, aby uzyskać najlepszą wydajność, zaleca się ustawienie jawnego **trybu XmlReadMode**zamiast akceptowania **domyślnego ustawienia automatycznego.**|  
|**ReadSchema ( ReadSchema )**|Odczytuje dowolny schemat wbudowany i ładuje dane i schemat.<br /><br /> Jeśli <xref:System.Data.DataSet> schemat zawiera już schemat, nowe tabele są dodawane ze schematu <xref:System.Data.DataSet>wbudowanego do istniejącego schematu w pliku . Jeśli istnieją już jakieś tabele w <xref:System.Data.DataSet>schemacie wbudowanym w , zostanie zgłoszony wyjątek. Nie będzie można zmodyfikować schematu istniejącej tabeli za pomocą **pliku XmlReadMode.ReadSchema**.<br /><br /> Jeśli <xref:System.Data.DataSet> nie zawiera schematu i nie ma schematu wbudowanego, nie są odczytywane żadne dane.<br /><br /> Schemat wbudowany można zdefiniować przy użyciu schematu języka XSD (XSD). Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [Wyprowadzanie struktury relacyjnej zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema (Ignorschema)**|Ignoruje schemat wbudowany i ładuje dane <xref:System.Data.DataSet> do istniejącego schematu. Wszystkie dane, które nie pasują do istniejącego schematu jest odrzucany. Jeśli w pliku , <xref:System.Data.DataSet>nie ma schematu, nie są ładowane żadne dane.<br /><br /> Jeśli dane są DiffGram, **IgnoreSchema** ma taką samą funkcjonalność jak **DiffGram** *.*|  
|**Inferschema**|Ignoruje schemat wbudowany i wywnioskować schemat na strukturę danych XML, a następnie ładuje dane.<br /><br /> Jeśli <xref:System.Data.DataSet> już zawiera schemat, bieżący schemat jest rozszerzany przez dodanie kolumn do istniejących tabel. Dodatkowe tabele nie zostaną dodane, jeśli nie istnieją istniejące tabele. Wyjątek jest zgłaszany, jeśli wywnioskowana tabela już istnieje z innym obszarem nazw lub jeśli jakieś wywnioskowane kolumny są w konflikcie z istniejącymi kolumnami.<br /><br /> Aby uzyskać szczegółowe informacje o tym, jak **program ReadXmlSchema** wylicza schemat z dokumentu XML, zobacz [Wnioskowanie struktury relacyjnej zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Formacie diffgram**|Odczytuje DiffGram i dodaje dane do bieżącego schematu. **DiffGram** scala nowe wiersze z istniejącymi wierszami, w których są zgodne wartości unikatowych identyfikatorów. Zobacz "Scalanie danych z XML" na końcu tego tematu. Aby uzyskać więcej informacji na temat DiffGramów, zobacz [DiffGrams](diffgrams.md).|  
|**Fragment**|Kontynuuje odczyt wielu fragmentów XML, aż do osiągnięcia końca strumienia. Fragmenty, które <xref:System.Data.DataSet> pasują do schematu są dołączane do odpowiednich tabel. Fragmenty, które nie <xref:System.Data.DataSet> pasują do schematu są odrzucane.|  
  
> [!NOTE]
> Jeśli przekażesz **XmlReader** do **ReadXml,** który jest pozycjonowany część drogi do dokumentu XML, **ReadXml** odczyta do następnego węzła elementu i będzie traktować to jako element główny, odczytu do końca węzła elementu tylko. Nie ma to zastosowania, jeśli określisz **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Jednostki DTD  
 Jeśli kod XML zawiera jednostki zdefiniowane w schemacie definicji typu dokumentu (DTD), wyjątek zostanie zgłoszony, jeśli spróbujesz załadować <xref:System.Data.DataSet> nazwę pliku, strumień lub niecepwalność **XmlReader** do **ReadXml**. Zamiast tego należy utworzyć **XmlValidatingReader,** z **EntityHandling** ustawiona na **EntityHandling.ExpandEntities**i przekazać **XmlValidatingReader** do **ReadXml**. **XmlValidatingReader** rozwinie jednostki przed odczytaniem <xref:System.Data.DataSet>przez .  
  
 Poniższe przykłady kodu pokazują, <xref:System.Data.DataSet> jak załadować ze strumienia XML. W pierwszym przykładzie jest wyświetlana nazwa pliku przekazywana do metody **ReadXml.** Drugi przykład pokazuje ciąg, który zawiera XML jest ładowany przy użyciu pliku <xref:System.IO.StringReader>.  
  
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
> Jeśli wywołasz **ReadXml,** aby załadować bardzo duży plik, może wystąpić niska wydajność. Aby zapewnić najlepszą wydajność **dla ReadXml**, <xref:System.Data.DataTable.BeginLoadData%2A> w dużym pliku, wywołaj metodę dla każdej tabeli w programie , a następnie wywołanie <xref:System.Data.DataSet> **ReadXml**. Na koniec <xref:System.Data.DataTable.EndLoadData%2A> wywołaj każdą <xref:System.Data.DataSet>tabelę w , jak pokazano w poniższym przykładzie.  
  
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
> Jeśli schemat XSD dla <xref:System.Data.DataSet> twojego zawiera **targetNamespace**, dane mogą nie być odczytywane i mogą <xref:System.Data.DataSet> wystąpić wyjątki, podczas wywoływania **ReadXml,** aby załadować z plikiem XML, który zawiera elementy bez kwalifikującego się obszaru nazw. Aby odczytać elementy niekwalifikowane w tym przypadku, ustaw **elementFormDefault** równa "kwalifikowany" w schemacie XSD. Przykład:  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Scalanie danych z XML  
 Jeśli <xref:System.Data.DataSet> już zawiera dane, nowe dane z XML są dodawane <xref:System.Data.DataSet>do danych już obecnych w . **ReadXml** nie scala się z <xref:System.Data.DataSet> pliku XML z żadnymi informacjami o wierszu z pasującymi kluczami podstawowymi. Aby zastąpić istniejące informacje o wierszu nowymi informacjami z xml, <xref:System.Data.DataSet>użyj <xref:System.Data.DataSet.Merge%2A> **ReadXml,** <xref:System.Data.DataSet>aby utworzyć nowy program , a następnie nowy <xref:System.Data.DataSet> w istniejącym pliku . Należy zauważyć, że ładowanie DiffGram przy użyciu **ReadXML** z **XmlReadMode** **DiffGram** scali wiersze, które mają ten sam unikatowy identyfikator.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DiffGram](diffgrams.md)
- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
