---
title: "Podczas ładowania zestawu danych z pliku XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d0c98224b8b508fec5fe584388872757a9dfdf3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="loading-a-dataset-from-xml"></a>Podczas ładowania zestawu danych z pliku XML
Zawartość ADO.NET <xref:System.Data.DataSet> mogą być tworzone z strumień XML lub dokument. Ponadto w środowisku .NET Framework masz dużą elastyczność w informacjach są ładowane z pliku XML i w jaki sposób schematu lub relacyjne struktury <xref:System.Data.DataSet> jest tworzony.  
  
 Aby wypełnić <xref:System.Data.DataSet> za pomocą danych z pliku XML, użyj **ReadXml** metody <xref:System.Data.DataSet> obiektu. **ReadXml** metoda odczytuje z pliku, typu stream, lub **XmlReader**i przyjmuje jako argumenty źródło XML oraz opcjonalny **XmlReadMode** argumentu. (Aby uzyskać więcej informacji na temat **XmlReader**, zobacz [NIB: odczytywanie danych XML za pomocą klasy XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) **ReadXml** metoda odczytuje zawartość strumienia XML lub dokument i obciążeń <xref:System.Data.DataSet> z danymi. Spowoduje również utworzenie schemat relacyjny <xref:System.Data.DataSet> w zależności od **XmlReadMode** określone i określa, czy schemat relacyjny już istnieje.  
  
 W poniższej tabeli opisano opcje **XmlReadMode** argumentu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Auto**|Domyślnie włączone. Sprawdza kod XML i wybierze najbardziej odpowiednią opcję w następującej kolejności:<br /><br /> — Jeśli kod XML jest elementu DiffGram **elementu DiffGram** jest używany.<br />-Jeśli <xref:System.Data.DataSet> zawiera schemat lub wbudowany schemat zawiera kod XML **ReadSchema** jest używany.<br />-Jeśli <xref:System.Data.DataSet> nie zawiera schemat i plik XML nie zawiera schemat wbudowany **InferSchema** jest używany.<br /><br /> Jeśli znasz format odczytywanego pliku XML, aby uzyskać najlepszą wydajność zaleca się ustawienie jawnego **XmlReadMode**, zamiast niż zaakceptować **automatycznie** domyślne.|  
|**ReadSchema**|Odczytuje wszystkie wbudowanego schematu i ładuje danych i schematu.<br /><br /> Jeśli <xref:System.Data.DataSet> już zawiera schemat, nowe tabele są dodawane z wbudowanego schematu istniejący schemat w <xref:System.Data.DataSet>. Jeśli wszystkie tabele w wbudowany schemat już istnieje w <xref:System.Data.DataSet>, jest zgłaszany wyjątek. Nie można zmodyfikować schemat istniejących przy użyciu tabeli **XmlReadMode.ReadSchema**.<br /><br /> Jeśli <xref:System.Data.DataSet> nie zawiera schematu, a nie Brak schemat wbudowany, nie są odczytywane dane.<br /><br /> Wbudowany schemat można zdefiniować przy użyciu schematu (XSD) języka definicji schematu XML. Aby uzyskać informacje na temat pisania wbudowanego schematu XML Schema, zobacz [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje wszystkie wbudowanego schematu i ładuje dane do istniejącego <xref:System.Data.DataSet> schematu. Dane, które nie pasuje do istniejącego schematu zostaną odrzucone. Jeśli schemat nie istnieje w <xref:System.Data.DataSet>, jest załadowane żadne dane.<br /><br /> Jeśli dane są elementu DiffGram **IgnoreSchema** ma te same funkcje co **elementu DiffGram** *.*|  
|**InferSchema**|Ignoruje wszystkie wbudowanego schematu i wnioskuje schemat na strukturze danych XML, a następnie ładuje dane.<br /><br /> Jeśli <xref:System.Data.DataSet> już zawiera schemat, bieżący schemat jest rozszerzony przez dodawanie kolumn do istniejących tabel. Dodatkowe tabele nie zostanie dodany, jeśli nie istnieją tabele. Jeśli wnioskowany tabela już istnieje z różnych przestrzeni nazw lub kolumn wnioskowany powodują konflikt z istniejących kolumn, jest zgłaszany wyjątek.<br /><br /> Aby uzyskać szczegółowe informacje o tym, jak **ReadXmlSchema** wnioskuje schemat dokumentu XML, zobacz temat [wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Odczytuje elementu DiffGram i dodaje je do bieżącego schematu. **Elementu DiffGram** scala nowe wiersze z istniejących wierszy, jeśli takie same wartości unikatowego identyfikatora. Zobacz "Scalanie danych z pliku XML" na końcu tego tematu. Aby uzyskać więcej informacji o DataSets, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Nadal odczytywania wielu fragmenty XML, aż do osiągnięcia końca strumienia. Fragmenty zgodnych <xref:System.Data.DataSet> schematu są dołączane do odpowiednich tabel. Fragmenty, które nie odpowiadają <xref:System.Data.DataSet> schematu zostaną odrzucone.|  
  
> [!NOTE]
>  W przypadku przekazania **XmlReader** do **ReadXml** będącego pozycjonowane częścią sposób w dokumencie XML **ReadXml** odczyta do następnego węzła elementu i będzie traktować który jako katalogu głównego Element Odczyt do końca tylko węzeł elementu. Nie dotyczy Jeśli określisz **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>DTD jednostek  
 Jeśli dane XML zawiera jednostki zdefiniowanej w schemacie definicji (DTD) typu dokumentu, będzie zgłaszany wyjątek, jeśli próba załadowania <xref:System.Data.DataSet> przez przekazanie pliku nazwy, strumienia lub bez weryfikacji **XmlReader** do  **ReadXml**. Zamiast tego należy utworzyć **elementu XmlValidatingReader**, z **EntityHandling** ustawioną **elementu EntityHandling.ExpandEntities**i przekazywać Twoje  **Elementu XmlValidatingReader** do **ReadXml**. **Elementu XmlValidatingReader** rozwinie jednostek przed odczytywany przez <xref:System.Data.DataSet>.  
  
 W poniższych przykładach kodu przedstawiają sposób załadować <xref:System.Data.DataSet> ze strumienia XML. W pierwszym przykładzie pokazano przekazywany do nazwy pliku **ReadXml** metody. Drugi przykład przedstawia ciąg, który zawiera XML jest załadować przy użyciu <xref:System.IO.StringReader>.  
  
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
>  Jeśli należy wywołać **ReadXml** załadować bardzo dużych plików, można napotkać niską wydajność. Aby zapewnić najlepszą wydajność dla **ReadXml**, na dużych plików, należy wywołać <xref:System.Data.DataTable.BeginLoadData%2A> metody dla każdej tabeli w <xref:System.Data.DataSet>, a następnie wywołać **ReadXml**. Na koniec wywołania <xref:System.Data.DataTable.EndLoadData%2A> dla każdej tabeli w <xref:System.Data.DataSet>, jak pokazano w poniższym przykładzie.  
  
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
>  Jeśli schematu XSD dla Twojego <xref:System.Data.DataSet> obejmuje **targetNamespace**, nie można odczytać danych i wyjątków, mogą wystąpić podczas wywoływania metody **ReadXml** załadować <xref:System.Data.DataSet> XML, który zawiera elementy bez kwalifikacji przestrzeni nazw. W takim przypadku odczytać niekwalifikowane elementy, ustaw **elementFormDefault** równa "kwalifikowana" schematu XSD. Na przykład:  
  
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
 Jeśli <xref:System.Data.DataSet> zawiera już dane, nowych danych z pliku XML jest dodana do danych znajduje się już w <xref:System.Data.DataSet>. **ReadXml** nie scalania z pliku XML do <xref:System.Data.DataSet> żadnego wiersza informacji ze zgodnymi kluczami podstawowymi. Aby zastąpić istniejące informacje wiersza z nowych informacji z pliku XML, użyj **ReadXml** do tworzenia nowego <xref:System.Data.DataSet>, a następnie <xref:System.Data.DataSet.Merge%2A> nowy <xref:System.Data.DataSet> do istniejącego <xref:System.Data.DataSet>. Należy pamiętać, że podczas ładowania elementu DiffGram przy użyciu **ReadXML** z **XmlReadMode** z **elementu DiffGram** będzie scalenie wierszy, które mają ten sam Unikatowy identyfikator.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
