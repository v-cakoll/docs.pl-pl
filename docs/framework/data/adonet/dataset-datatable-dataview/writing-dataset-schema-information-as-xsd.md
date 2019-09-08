---
title: Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784182"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD
Można napisać schemat <xref:System.Data.DataSet> programu jako schemat języka definicji schematu XML (XSD), dzięki czemu można transportować go z lub bez powiązanych danych w dokumencie XML. Schemat XML można zapisać w pliku, strumieniu, <xref:System.Xml.XmlWriter>a lub ciągu; jest to przydatne w przypadku generowania **zestawu danych**o jednoznacznie określonym typie. Aby uzyskać więcej informacji na temat obiektów typu **zestaw danych** o jednoznacznie określonym typie, zobacz [zestawy danych z określonym typem](typed-datasets.md).  
  
 Można określić sposób, w jaki kolumna tabeli jest reprezentowana w schemacie XML przy użyciu właściwości <xref:System.Data.DataColumn> ColumnMapping obiektu. Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn do elementów XML, atrybutów i tekstu" w [treści zestawu danych jako dane XML](writing-dataset-contents-as-xml-data.md).  
  
 Aby zapisać schemat **zestawu danych** jako schemat XML, do pliku, strumienia lub **XmlWriter**, użyj metody **WriteXmlSchema** **zestawu danych**. **WriteXmlSchema** przyjmuje jeden parametr, który określa miejsce docelowe uzyskanego schematu XML. Poniższy przykład kodu pokazuje, jak napisać schemat XML **zestawu danych** do pliku, przekazując ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiekt.  
  
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
  
 Aby uzyskać schemat **zestawu danych** i zapisać go jako ciąg schematu XML, należy **użyć metody GetXml,** jak pokazano w poniższym przykładzie.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Zapisywanie zawartości elementu DataSet jako danych XML](writing-dataset-contents-as-xml-data.md)
- [Typizowane elementy DataSet](typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
