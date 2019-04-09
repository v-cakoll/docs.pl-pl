---
title: Zapisywanie zawartości elementu DataSet jako danych XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: dae044a9d7802e858f1f24dd4aa0f1de8f6cba7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158955"
---
# <a name="writing-dataset-contents-as-xml-data"></a>Zapisywanie zawartości elementu DataSet jako danych XML
W ADO.NET można napisać Reprezentacja XML <xref:System.Data.DataSet>, z lub bez jego schematu. Informacje o schemacie jest uwzględnione w tekście z pliku XML, jest ona zapisywana, za pomocą języka definicji schematu XML (XSD). Schemat zawiera definicje tabeli <xref:System.Data.DataSet> oraz definicje relacja i ograniczenie.  
  
 Gdy <xref:System.Data.DataSet> jest zapisywany jako danych XML, wiersze <xref:System.Data.DataSet> są zapisywane w ich bieżącej wersji. Jednak <xref:System.Data.DataSet> można również zapisać jako element w formacie DiffGram tak, aby bieżące i oryginalne wartości parametru wiersze zostaną dołączone.  
  
 Reprezentacja XML <xref:System.Data.DataSet> mogą być zapisywane do pliku strumienia, **XmlWriter**, lub ciągiem. Te opcje zapewniają dużą elastyczność dla jak transportu reprezentację XML <xref:System.Data.DataSet>. Aby uzyskać reprezentację XML <xref:System.Data.DataSet> jako ciąg znaków, należy użyć **getxml —** metody, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **Getxml —** zwraca reprezentację XML <xref:System.Data.DataSet> bez informacji o schemacie. Można zapisać informacji o schemacie z <xref:System.Data.DataSet> (jako schematu XML) na ciąg, użyj **GetXmlSchema**.  
  
 Można zapisać <xref:System.Data.DataSet> w pliku strumienia, lub **XmlWriter**, użyj **WriteXml** metody. Pierwszy parametr, które są przekazywane do **WriteXml** jest miejscem docelowym danych wyjściowych XML. Na przykład przekazać ciąg zawierający nazwę pliku **System.IO.TextWriter** obiektu i tak dalej. Można przekazać opcjonalny drugi parametr funkcji **XmlWriteMode** do określenia, jak dane wyjściowe XML jest do zapisania.  
  
 W poniższej tabeli przedstawiono opcje **XmlWriteMode**.  
  
|Opcja XmlWriteMode|Opis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapisuje zawartość bieżącego <xref:System.Data.DataSet> jako danych XML bez schematu XML. Domyślnie włączone.|  
|**WriteSchema**|Zapisuje zawartość bieżącego <xref:System.Data.DataSet> jako danych XML przy użyciu relacyjnej struktury jako wbudowanego schematu XML.|  
|**Format DiffGram**|Zapisuje całą <xref:System.Data.DataSet> jako element w formacie DiffGram, łącznie z pierwotnym i bieżącym wartości. Aby uzyskać więcej informacji, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Podczas zapisywania zawartości reprezentację XML <xref:System.Data.DataSet> zawierający **DataRelation** obiektów, najprawdopodobniej będą wynikowy kod XML ma wiersze podrzędne każdej relacji zagnieżdżone w obrębie ich elementy nadrzędne powiązane. Aby to zrobić, należy ustawić **zagnieżdżone** właściwość **DataRelation** do **true** po dodaniu **DataRelation** do <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Poniżej przedstawiono dwa przykłady sposobu pisania reprezentację XML <xref:System.Data.DataSet> do pliku. Pierwszy przykład przekazuje nazwę pliku dla wynikowy kod XML jako ciąg do **WriteXml**. Drugi przykład przekazuje **System.IO.StreamWriter** obiektu.  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapowanie kolumn do elementów XML, atrybuty i tekstu  
 Można określić, jak kolumny tabeli są reprezentowane w formacie XML przy użyciu **ColumnMapping** właściwość **DataColumn** obiektu. W poniższej tabeli przedstawiono poszczególne **MappingType** wartości **ColumnMapping** właściwość kolumny tabeli i wynikowy kod XML.  
  
|Wartość MappingType|Opis|  
|-----------------------|-----------------|  
|**Element**|Domyślnie włączone. Kolumny są zapisywane jako XML element, gdzie ColumnName jest nazwa elementu, a zawartość kolumny są zapisywane w postaci tekstu elementu. Na przykład:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atrybut**|Kolumny są zapisywane jako atrybut XML elementu XML dla bieżącego wiersza, gdzie ColumnName jest nazwa atrybutu, a zawartość kolumny są zapisywane jako wartość atrybutu. Na przykład:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Zawartość kolumny są zapisywane jako tekst w elemencie XML dla bieżącego wiersza. Na przykład:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Należy pamiętać, że **SimpleContent** nie można ustawić wartości w kolumnie tabeli, która ma **elementu** kolumn ani relacjach zagnieżdżonych.|  
|**Hidden**|Kolumna nie jest zapisywana w danych wyjściowych XML.|  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [Zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
