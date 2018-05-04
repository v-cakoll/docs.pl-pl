---
title: Zapisywanie informacji o schemacie zestawu danych jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: b2012b32b0751bc093b9b3267cbbfc2e1a408156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zapisywanie informacji o schemacie zestawu danych jako XSD
Schemat można napisać <xref:System.Data.DataSet> schematu XML Schema (XSD) języka definicji, dzięki czemu można przetransportować go, lub bez powiązane dane w dokumencie XML. Schemat XML można zapisać pliku, typu stream, <xref:System.Xml.XmlWriter>, lub ciąg; jest przydatne w przypadku generowania silnie typizowaną **zestawu danych**. Aby uzyskać więcej informacji na temat silnie typizowane **DataSet** obiekty, zobacz [wpisanych zestawów danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Można określić, jak kolumny tabeli są reprezentowane w schemacie XML przy użyciu **ColumnMapping** właściwość <xref:System.Data.DataColumn> obiektu. Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn XML elementy, atrybuty i tekst" w [zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Można zapisać schemat **DataSet** jako schematu XML w pliku strumienia, lub **XmlWriter**, użyj **WriteXmlSchema** metody **zestawu danych**. **WriteXmlSchema** przyjmuje jeden parametr, który określa lokalizację docelową wynikowy schematu XML. W poniższych przykładach kodu przedstawiają sposób zapisu schemat XML **DataSet** w pliku przez przekazanie ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiektu.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Można uzyskać schematu elementu **DataSet** i zapisać go jako ciąg schematu XML, użyj **GetXmlSchema** metody, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
