---
title: Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 8403f9d9be88f34e473fd3512f5499193245d227
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099446"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD
Można napisać schemat <xref:System.Data.DataSet> jako schematu języka (XSD) definicji schematu XML, dzięki czemu mogą transportować, z lub bez powiązanych danych w dokumencie XML. Schemat XML mogą być zapisywane do pliku strumienia, <xref:System.Xml.XmlWriter>, lub ciąg; jest to przydatne podczas generowania silnie typizowanej **zestawu danych**. Aby uzyskać więcej informacji na temat silnie typizowane **DataSet** obiekty, zobacz [wpisanych zestawów danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Można określić, jak kolumny tabeli jest reprezentowana w schemacie XML przy użyciu **ColumnMapping** właściwość <xref:System.Data.DataColumn> obiektu. Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn do elementów XML, atrybuty i tekst" w [zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Można zapisać schematu **DataSet** jako schematu XML w pliku strumienia, lub **XmlWriter**, użyj **WriteXmlSchema** metody **zestawu danych**. **WriteXmlSchema** przyjmuje jeden parametr, który określa miejsce docelowe wynikowy schematu XML. Poniższe przykłady kodu przedstawiają sposób zapisu schemat XML **DataSet** do pliku, przekazując ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiektu.  
  
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
  
 Można uzyskać schematu **DataSet** i zapisz je jako ciąg schematu XML, należy użyć **GetXmlSchema** metodzie, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
