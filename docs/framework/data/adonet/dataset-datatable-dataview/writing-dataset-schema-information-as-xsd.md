---
title: Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072816"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="42e7a-102">Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD</span><span class="sxs-lookup"><span data-stu-id="42e7a-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="42e7a-103">Można napisać schemat <xref:System.Data.DataSet> jako schematu języka (XSD) definicji schematu XML, dzięki czemu mogą transportować, z lub bez powiązanych danych w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="42e7a-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="42e7a-104">Schemat XML mogą być zapisywane do pliku strumienia, <xref:System.Xml.XmlWriter>, lub ciąg; jest to przydatne podczas generowania silnie typizowanej **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="42e7a-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="42e7a-105">Aby uzyskać więcej informacji na temat silnie typizowane **DataSet** obiekty, zobacz [wpisanych zestawów danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="42e7a-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="42e7a-106">Można określić, jak kolumny tabeli jest reprezentowana w schemacie XML przy użyciu **ColumnMapping** właściwość <xref:System.Data.DataColumn> obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e7a-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="42e7a-107">Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn do elementów XML, atrybuty i tekst" w [zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="42e7a-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="42e7a-108">Można zapisać schematu **DataSet** jako schematu XML w pliku strumienia, lub **XmlWriter**, użyj **WriteXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="42e7a-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="42e7a-109">**WriteXmlSchema** przyjmuje jeden parametr, który określa miejsce docelowe wynikowy schematu XML.</span><span class="sxs-lookup"><span data-stu-id="42e7a-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="42e7a-110">Poniższe przykłady kodu przedstawiają sposób zapisu schemat XML **DataSet** do pliku, przekazując ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="42e7a-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="42e7a-111">Można uzyskać schematu **DataSet** i zapisz je jako ciąg schematu XML, należy użyć **GetXmlSchema** metodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42e7a-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="42e7a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42e7a-112">See Also</span></span>  
 [<span data-ttu-id="42e7a-113">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="42e7a-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="42e7a-114">Zapisywanie zawartości elementu DataSet jako danych XML</span><span class="sxs-lookup"><span data-stu-id="42e7a-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="42e7a-115">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="42e7a-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="42e7a-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="42e7a-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="42e7a-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="42e7a-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
