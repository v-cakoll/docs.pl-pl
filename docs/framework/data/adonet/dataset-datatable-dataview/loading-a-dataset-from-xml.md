---
title: Ładowanie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0c53e3a15bcbe61db7da1edb31ecd3fd562603f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099901"
---
# <a name="loading-a-dataset-from-xml"></a>Ładowanie elementu DataSet z pliku XML
Zawartość ADO.NET <xref:System.Data.DataSet> można tworzyć na podstawie strumień XML lub dokumentu. Ponadto, za pomocą programu .NET Framework masz dużą elastyczność w informacjach jest ładowany z pliku XML i w jaki sposób schematu lub relacyjnej struktury elementu <xref:System.Data.DataSet> zostanie utworzony.  
  
 Aby wypełnić <xref:System.Data.DataSet> z danymi z pliku XML, należy użyć **ReadXml** metody <xref:System.Data.DataSet> obiektu. **ReadXml** metoda odczytuje z pliku strumienia, lub **XmlReader**i przyjmuje jako argumenty źródła XML oraz opcjonalnie **XmlReadMode** argumentu. Aby uzyskać więcej informacji na temat **XmlReader**, zobacz [odczytywania danych XML przy użyciu klasy XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). **ReadXml** metoda odczytuje zawartość strumienia XML lub dokumentu i obciążeniami <xref:System.Data.DataSet> z danymi. Utworzy on również schemat relacyjnej <xref:System.Data.DataSet> w zależności od **XmlReadMode** określona, czy schemat relacyjny już istnieje.  
  
 W poniższej tabeli opisano opcje **XmlReadMode** argumentu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Auto**|Domyślnie włączone. Sprawdza, czy plik XML i wybierze najbardziej odpowiednią opcję w następującej kolejności:<br /><br /> — Jeśli plik XML jest w formacie DiffGram, **w formacie DiffGram** jest używany.<br />-Jeśli <xref:System.Data.DataSet> zawiera schemat lub plik XML zawiera schemat wbudowany **ReadSchema** jest używany.<br />-Jeśli <xref:System.Data.DataSet> nie zawiera schemat i dane XML nie zawiera schemat wbudowany **InferSchema** jest używany.<br /><br /> Jeśli znasz format XML, odczytu, aby uzyskać najlepszą wydajność zalecane jest ustawienie jawnego **XmlReadMode**, a nie akceptują **automatycznie** domyślne.|  
|**ReadSchema**|Odczytuje schemat w tekście i ładuje schemat i dane.<br /><br /> Jeśli <xref:System.Data.DataSet> już zawiera schemat, nowe tabele są dodawane od wbudowanego schematu do istniejącego schematu w <xref:System.Data.DataSet>. Jeśli wszystkie tabele w wbudowanego schematu jest już istnieją w <xref:System.Data.DataSet>, zgłaszany jest wyjątek. Nie można zmodyfikować schemat z istniejącej tabeli przy użyciu **XmlReadMode.ReadSchema**.<br /><br /> Jeśli <xref:System.Data.DataSet> nie zawiera schematu i istnieje żaden schemat wbudowany, nie są odczytywane dane.<br /><br /> Schemat w tekście można zdefiniować przy użyciu schematu języka (XSD) definicji schematu XML. Aby uzyskać informacje na temat pisania wbudowanego schematu XML Schema zobacz [elementu pochodnego dla zestawu danych relacyjnej struktury z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje wszelkie wbudowanego schematu i ładuje dane do istniejącego <xref:System.Data.DataSet> schematu. Wszelkie dane, które nie jest zgodny ze schematem istniejących jest odrzucany. Jeśli żaden schemat nie istnieje w <xref:System.Data.DataSet>, nie dane są ładowane.<br /><br /> Jeśli dane są w formacie DiffGram, **IgnoreSchema** ma taką samą funkcjonalność jak **w formacie DiffGram** *.*|  
|**InferSchema**|Ignoruje wszelkie wbudowanego schematu i wnioskuje schemat na strukturę danych XML, a następnie ładuje dane.<br /><br /> Jeśli <xref:System.Data.DataSet> już zawiera schemat bieżącego schemat został rozszerzony, dodając kolumny do istniejących tabel. Dodatkowe tabele nie zostanie dodany, jeśli nie istnieją tabele. Wyjątek jest generowany, jeśli wywnioskowane tabela już istnieje z innej przestrzeni nazw lub wywnioskowane kolumn w konflikcie z istniejących kolumn.<br /><br /> Aby uzyskać szczegółowe informacje o tym, jak **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz [wnioskowanie zestawu danych relacyjnej struktury z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**Format DiffGram**|Odczytuje element w formacie DiffGram i dodaje je do bieżącego schematu. **Format DiffGram** scala nowych wierszy przy użyciu istniejących wierszy, jeśli są takie same wartości unikatowego identyfikatora. Zobacz "Scalania danych z pliku XML" na końcu tego tematu. Aby uzyskać więcej informacji na temat DataSets zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Nadal odczytywanie wiele fragmenty XML, aż do osiągnięcia końca strumienia. Liczba fragmentów, które pasują do <xref:System.Data.DataSet> schematu są dołączane do odpowiednich tabel. Fragmenty, które nie odpowiadają <xref:System.Data.DataSet> schematu są odrzucane.|  
  
> [!NOTE]
>  W przypadku przekazania **XmlReader** do **ReadXml** będącego pozycjonowane częścią sposób do dokumentu XML, **ReadXml** odczyta do kolejnego węzła elementu i traktują, jako katalog główny Element odczytywanie aż do końca tylko węzeł elementu. To nie ma zastosowania w przypadku określenia **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Jednostkami DTD  
 Jeśli dane XML zawiera jednostki zdefiniowanej w schemacie definition (DTD) typu dokumentu, wyjątek zostanie zgłoszony, jeśli użytkownik podejmie próbę załadowania <xref:System.Data.DataSet> przez przekazanie pliku nazwa strumienia i bez weryfikacji **XmlReader** do  **ReadXml**. Zamiast tego należy utworzyć **elementu XmlValidatingReader**, za pomocą **EntityHandling** równa **elementu EntityHandling.ExpandEntities**i przekazać swoje  **Elementu XmlValidatingReader** do **ReadXml**. **Elementu XmlValidatingReader** rozwinie jednostek przed odczytywany przez <xref:System.Data.DataSet>.  
  
 W poniższych przykładach kodu pokazano sposób ładowania <xref:System.Data.DataSet> ze strumienia XML. Pierwszy przykład przedstawia nazwę pliku, który został przekazany do **ReadXml** metody. Drugi przykład przedstawia ciąg, który zawiera załadowane, przy użyciu zwrócenia XML <xref:System.IO.StringReader>.  
  
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
>  Jeśli wywołasz **ReadXml** załadować bardzo dużych plików, mogą wystąpić spadek wydajności. Aby zapewnić najlepszą wydajność dla **ReadXml**, na dużych plików, należy wywołać <xref:System.Data.DataTable.BeginLoadData%2A> metody dla każdej tabeli w <xref:System.Data.DataSet>, a następnie wywołaj **ReadXml**. Na koniec Wywołaj <xref:System.Data.DataTable.EndLoadData%2A> dla każdej tabeli w <xref:System.Data.DataSet>, jak pokazano w poniższym przykładzie.  
  
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
>  Jeśli schemat XSD dla Twojej <xref:System.Data.DataSet> obejmuje **przestrzeni nazw targetNamespace**, nie można odczytać danych i wyjątków, mogą wystąpić podczas wywoływania **ReadXml** załadować <xref:System.Data.DataSet> z danymi XML, który zawiera elementy z nie kwalifikującym się przestrzenią nazw. Aby odczytać elementy niekwalifikowane w tym przypadku, należy ustawić **elementFormDefault** równym "kwalifikowany" schematu XSD. Na przykład:  
  
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
 Jeśli <xref:System.Data.DataSet> zawiera już dane, nowe dane z pliku XML jest dodawany do danych już istnieje w <xref:System.Data.DataSet>. **ReadXml** scalać z pliku XML do <xref:System.Data.DataSet> dowolny wiersz informacji ze zgodnymi kluczami podstawowymi. Aby zastąpić istniejące informacje wiersza przy użyciu nowych informacji z pliku XML, należy użyć **ReadXml** do tworzenia nowego <xref:System.Data.DataSet>, a następnie <xref:System.Data.DataSet.Merge%2A> nowy <xref:System.Data.DataSet> się z istniejącymi <xref:System.Data.DataSet>. Należy pamiętać, że załadowanie w formacie DiffGram przy użyciu **ReadXML** z **XmlReadMode** z **w formacie DiffGram** spowoduje scalenie wierszy, które mają taki sam Unikatowy identyfikator.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
