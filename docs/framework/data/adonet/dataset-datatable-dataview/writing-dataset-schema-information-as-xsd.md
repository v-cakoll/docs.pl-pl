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
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="3aa34-102">Zapisywanie informacji o schemacie zestawu danych jako XSD</span><span class="sxs-lookup"><span data-stu-id="3aa34-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="3aa34-103">Schemat można napisać <xref:System.Data.DataSet> schematu XML Schema (XSD) języka definicji, dzięki czemu można przetransportować go, lub bez powiązane dane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="3aa34-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="3aa34-104">Schemat XML można zapisać pliku, typu stream, <xref:System.Xml.XmlWriter>, lub ciąg; jest przydatne w przypadku generowania silnie typizowaną **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3aa34-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="3aa34-105">Aby uzyskać więcej informacji na temat silnie typizowane **DataSet** obiekty, zobacz [wpisanych zestawów danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="3aa34-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="3aa34-106">Można określić, jak kolumny tabeli są reprezentowane w schemacie XML przy użyciu **ColumnMapping** właściwość <xref:System.Data.DataColumn> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3aa34-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="3aa34-107">Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn XML elementy, atrybuty i tekst" w [zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="3aa34-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="3aa34-108">Można zapisać schemat **DataSet** jako schematu XML w pliku strumienia, lub **XmlWriter**, użyj **WriteXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="3aa34-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="3aa34-109">**WriteXmlSchema** przyjmuje jeden parametr, który określa lokalizację docelową wynikowy schematu XML.</span><span class="sxs-lookup"><span data-stu-id="3aa34-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="3aa34-110">W poniższych przykładach kodu przedstawiają sposób zapisu schemat XML **DataSet** w pliku przez przekazanie ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3aa34-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="3aa34-111">Można uzyskać schematu elementu **DataSet** i zapisać go jako ciąg schematu XML, użyj **GetXmlSchema** metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3aa34-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aa34-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3aa34-112">See Also</span></span>  
 [<span data-ttu-id="3aa34-113">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="3aa34-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="3aa34-114">Zapisywanie zawartości elementu DataSet jako danych XML</span><span class="sxs-lookup"><span data-stu-id="3aa34-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="3aa34-115">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="3aa34-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="3aa34-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="3aa34-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3aa34-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3aa34-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
