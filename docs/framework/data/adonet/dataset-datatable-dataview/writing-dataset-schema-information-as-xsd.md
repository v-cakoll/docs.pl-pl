---
title: Zapisywanie informacji o schemacie zestawu danych jako XSD
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
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bea961310c838068a54f15f7b05186ab56721dc2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="2a0cb-102">Zapisywanie informacji o schemacie zestawu danych jako XSD</span><span class="sxs-lookup"><span data-stu-id="2a0cb-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="2a0cb-103">Schemat można napisać <xref:System.Data.DataSet> schematu XML Schema (XSD) języka definicji, dzięki czemu można przetransportować go, lub bez powiązane dane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="2a0cb-104">Schemat XML można zapisać pliku, typu stream, <xref:System.Xml.XmlWriter>, lub ciąg; jest przydatne w przypadku generowania silnie typizowaną **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="2a0cb-105">Aby uzyskać więcej informacji na temat silnie typizowane **DataSet** obiekty, zobacz [wpisanych zestawów danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="2a0cb-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="2a0cb-106">Można określić, jak kolumny tabeli są reprezentowane w schemacie XML przy użyciu **ColumnMapping** właściwość <xref:System.Data.DataColumn> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="2a0cb-107">Aby uzyskać więcej informacji, zobacz "Mapowanie kolumn XML elementy, atrybuty i tekst" w [zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="2a0cb-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="2a0cb-108">Można zapisać schemat **DataSet** jako schematu XML w pliku strumienia, lub **XmlWriter**, użyj **WriteXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="2a0cb-109">**WriteXmlSchema** przyjmuje jeden parametr, który określa lokalizację docelową wynikowy schematu XML.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="2a0cb-110">W poniższych przykładach kodu przedstawiają sposób zapisu schemat XML **DataSet** w pliku przez przekazanie ciąg zawierający nazwę pliku i <xref:System.IO.StreamWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="2a0cb-111">Można uzyskać schematu elementu **DataSet** i zapisać go jako ciąg schematu XML, użyj **GetXmlSchema** metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2a0cb-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a0cb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a0cb-112">See Also</span></span>  
 [<span data-ttu-id="2a0cb-113">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="2a0cb-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="2a0cb-114">Zapisywanie zawartości elementu DataSet jako danych XML</span><span class="sxs-lookup"><span data-stu-id="2a0cb-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="2a0cb-115">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="2a0cb-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="2a0cb-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="2a0cb-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="2a0cb-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="2a0cb-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
