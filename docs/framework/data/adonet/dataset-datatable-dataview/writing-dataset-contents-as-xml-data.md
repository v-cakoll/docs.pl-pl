---
title: "Zapisywanie zawartości zestawu danych jako dane XML"
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
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b1250d616ad5835fccd1a3acbf0b8a759c34181
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-contents-as-xml-data"></a>Zapisywanie zawartości zestawu danych jako dane XML
W ADO.NET można zapisywać reprezentację XML <xref:System.Data.DataSet>, z lub bez jego schematu. Informacje o schemacie są uwzględniane wbudowany z pliku XML, jest ona zapisywana, przy użyciu języka definicji schematu XML (XSD). Schemat zawiera definicje tabel <xref:System.Data.DataSet> oraz definicje relacja i ograniczenie.  
  
 Gdy <xref:System.Data.DataSet> są zapisywane jako wiersze w danych XML <xref:System.Data.DataSet> są zapisywane w ich bieżącej wersji. Jednak <xref:System.Data.DataSet> również mogą być zapisywane jako elementu DiffGram, dzięki czemu zarówno bieżące i oryginalne wartości wierszy zostanie uwzględniony.  
  
 Reprezentacja XML <xref:System.Data.DataSet> mogą być zapisywane do pliku, typu stream, **XmlWriter**, lub ciągiem. Te opcje zapewniają elastyczność dla jak transportu reprezentację XML <xref:System.Data.DataSet>. Aby uzyskać reprezentację XML <xref:System.Data.DataSet> jako ciąg, użyj **GetXml** — metoda, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** zwraca reprezentację XML <xref:System.Data.DataSet> bez informacji o schemacie. Można zapisać informacji o schemacie z <xref:System.Data.DataSet> (jako schematu XML) na ciąg, użyj **GetXmlSchema**.  
  
 Można zapisać <xref:System.Data.DataSet> do pliku, stream, lub **XmlWriter**, użyj **WriteXml** metody. Pierwszy parametr przekazywany do **WriteXml** jest miejsce docelowe danych wyjściowych XML. Na przykład przekazuje ciąg zawierający nazwę pliku **System.IO.TextWriter** obiektu i tak dalej. Można przekazać Opcjonalnie drugi parametr funkcji **XmlWriteMode** można określić, jak dane wyjściowe XML jest do zapisania.  
  
 W poniższej tabeli przedstawiono opcje **XmlWriteMode**.  
  
|Opcja XmlWriteMode|Opis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapisuje bieżącą zawartość <xref:System.Data.DataSet> danych XML bez schematu XML. Domyślnie włączone.|  
|**WriteSchema**|Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML ze strukturą relacyjne jako wbudowanego schematu XML.|  
|**DiffGram**|Zapisuje całą <xref:System.Data.DataSet> jako elementu DiffGram tym oryginalny i bieżące wartości. Aby uzyskać więcej informacji, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Podczas zapisywania reprezentację XML <xref:System.Data.DataSet> zawierający **DataRelation** obiekty, najprawdopodobniej będziesz wynikowy kod XML ma wierszy podrzędnych każdej relacji zagnieżdżone w obrębie ich elementów nadrzędnych pokrewne. Aby to zrobić, ustaw **zagnieżdżone** właściwość **DataRelation** do **true** po dodaniu **DataRelation** do <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [zagnieżdżania DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Poniżej przedstawiono dwa przykłady sposobu pisania reprezentację XML <xref:System.Data.DataSet> do pliku. Pierwszym przykładzie przekazuje nazwę pliku wynikowego XML jako ciąg, aby **WriteXml**. Drugi przykład przekazuje **System.IO.StreamWriter** obiektu.  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapowanie kolumny do elementów XML i atrybuty tekstu  
 Można określić, jak kolumny tabeli są reprezentowane w formacie XML przy użyciu **ColumnMapping** właściwość **DataColumn** obiektu. W poniższej tabeli przedstawiono różne **MappingType** wartości **ColumnMapping** właściwość kolumnie tabeli, a wynikowy kod XML.  
  
|Wartość MappingType|Opis|  
|-----------------------|-----------------|  
|**Element**|Domyślnie włączone. Kolumny są zapisywane jako elementu XML, gdy element ColumnName jest nazwa elementu i zawartości kolumny są zapisywane jako tekst elementu. Na przykład:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atrybut**|Kolumny są zapisywane jako atrybut XML elementu XML dla bieżącego wiersza, w którym element ColumnName jest nazwa atrybutu i zawartości kolumny są zapisywane jako wartość atrybutu. Na przykład:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Zawartość kolumny są zapisywane jako tekst w elemencie XML dla bieżącego wiersza. Na przykład:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Należy pamiętać, że **SimpleContent** nie można ustawić wartości w kolumnie tabeli, która ma **elementu** kolumn lub relacje zagnieżdżone.|  
|**Ukryte**|Kolumna nie jest zapisywany w danych wyjściowych XML.|  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
