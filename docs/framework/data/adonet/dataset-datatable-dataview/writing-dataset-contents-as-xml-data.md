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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8c28dee75d5371da50dec1d3b73ec6c305176582
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="15e90-102">Zapisywanie zawartości zestawu danych jako dane XML</span><span class="sxs-lookup"><span data-stu-id="15e90-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="15e90-103">W ADO.NET można zapisywać reprezentację XML <xref:System.Data.DataSet>, z lub bez jego schematu.</span><span class="sxs-lookup"><span data-stu-id="15e90-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="15e90-104">Informacje o schemacie są uwzględniane wbudowany z pliku XML, jest ona zapisywana, przy użyciu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="15e90-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="15e90-105">Schemat zawiera definicje tabel <xref:System.Data.DataSet> oraz definicje relacja i ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="15e90-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="15e90-106">Gdy <xref:System.Data.DataSet> są zapisywane jako wiersze w danych XML <xref:System.Data.DataSet> są zapisywane w ich bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="15e90-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="15e90-107">Jednak <xref:System.Data.DataSet> również mogą być zapisywane jako elementu DiffGram, dzięki czemu zarówno bieżące i oryginalne wartości wierszy zostanie uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="15e90-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="15e90-108">Reprezentacja XML <xref:System.Data.DataSet> mogą być zapisywane do pliku, typu stream, **XmlWriter**, lub ciągiem.</span><span class="sxs-lookup"><span data-stu-id="15e90-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="15e90-109">Te opcje zapewniają elastyczność dla jak transportu reprezentację XML <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="15e90-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="15e90-110">Aby uzyskać reprezentację XML <xref:System.Data.DataSet> jako ciąg, użyj **GetXml** — metoda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15e90-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="15e90-111">**GetXml** zwraca reprezentację XML <xref:System.Data.DataSet> bez informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="15e90-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="15e90-112">Można zapisać informacji o schemacie z <xref:System.Data.DataSet> (jako schematu XML) na ciąg, użyj **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="15e90-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="15e90-113">Można zapisać <xref:System.Data.DataSet> do pliku, stream, lub **XmlWriter**, użyj **WriteXml** metody.</span><span class="sxs-lookup"><span data-stu-id="15e90-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="15e90-114">Pierwszy parametr przekazywany do **WriteXml** jest miejsce docelowe danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="15e90-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="15e90-115">Na przykład przekazuje ciąg zawierający nazwę pliku **System.IO.TextWriter** obiektu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="15e90-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="15e90-116">Można przekazać Opcjonalnie drugi parametr funkcji **XmlWriteMode** można określić, jak dane wyjściowe XML jest do zapisania.</span><span class="sxs-lookup"><span data-stu-id="15e90-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="15e90-117">W poniższej tabeli przedstawiono opcje **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="15e90-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="15e90-118">Opcja XmlWriteMode</span><span class="sxs-lookup"><span data-stu-id="15e90-118">XmlWriteMode option</span></span>|<span data-ttu-id="15e90-119">Opis</span><span class="sxs-lookup"><span data-stu-id="15e90-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="15e90-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="15e90-120">**IgnoreSchema**</span></span>|<span data-ttu-id="15e90-121">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> danych XML bez schematu XML.</span><span class="sxs-lookup"><span data-stu-id="15e90-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="15e90-122">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="15e90-122">This is the default.</span></span>|  
|<span data-ttu-id="15e90-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="15e90-123">**WriteSchema**</span></span>|<span data-ttu-id="15e90-124">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML ze strukturą relacyjne jako wbudowanego schematu XML.</span><span class="sxs-lookup"><span data-stu-id="15e90-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="15e90-125">**Elementu DiffGram**</span><span class="sxs-lookup"><span data-stu-id="15e90-125">**DiffGram**</span></span>|<span data-ttu-id="15e90-126">Zapisuje całą <xref:System.Data.DataSet> jako elementu DiffGram tym oryginalny i bieżące wartości.</span><span class="sxs-lookup"><span data-stu-id="15e90-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="15e90-127">Aby uzyskać więcej informacji, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="15e90-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="15e90-128">Podczas zapisywania reprezentację XML <xref:System.Data.DataSet> zawierający **DataRelation** obiekty, najprawdopodobniej będziesz wynikowy kod XML ma wierszy podrzędnych każdej relacji zagnieżdżone w obrębie ich elementów nadrzędnych pokrewne.</span><span class="sxs-lookup"><span data-stu-id="15e90-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="15e90-129">Aby to zrobić, ustaw **zagnieżdżone** właściwość **DataRelation** do **true** po dodaniu **DataRelation** do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="15e90-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="15e90-130">Aby uzyskać więcej informacji, zobacz [zagnieżdżania DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="15e90-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="15e90-131">Poniżej przedstawiono dwa przykłady sposobu pisania reprezentację XML <xref:System.Data.DataSet> do pliku.</span><span class="sxs-lookup"><span data-stu-id="15e90-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="15e90-132">Pierwszym przykładzie przekazuje nazwę pliku wynikowego XML jako ciąg, aby **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="15e90-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="15e90-133">Drugi przykład przekazuje **System.IO.StreamWriter** obiektu.</span><span class="sxs-lookup"><span data-stu-id="15e90-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="15e90-134">Mapowanie kolumny do elementów XML i atrybuty tekstu</span><span class="sxs-lookup"><span data-stu-id="15e90-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="15e90-135">Można określić, jak kolumny tabeli są reprezentowane w formacie XML przy użyciu **ColumnMapping** właściwość **DataColumn** obiektu.</span><span class="sxs-lookup"><span data-stu-id="15e90-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="15e90-136">W poniższej tabeli przedstawiono różne **MappingType** wartości **ColumnMapping** właściwość kolumnie tabeli, a wynikowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="15e90-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="15e90-137">Wartość MappingType</span><span class="sxs-lookup"><span data-stu-id="15e90-137">MappingType value</span></span>|<span data-ttu-id="15e90-138">Opis</span><span class="sxs-lookup"><span data-stu-id="15e90-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="15e90-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="15e90-139">**Element**</span></span>|<span data-ttu-id="15e90-140">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="15e90-140">This is the default.</span></span> <span data-ttu-id="15e90-141">Kolumny są zapisywane jako elementu XML, gdy element ColumnName jest nazwa elementu i zawartości kolumny są zapisywane jako tekst elementu.</span><span class="sxs-lookup"><span data-stu-id="15e90-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="15e90-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="15e90-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="15e90-143">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="15e90-143">**Attribute**</span></span>|<span data-ttu-id="15e90-144">Kolumny są zapisywane jako atrybut XML elementu XML dla bieżącego wiersza, w którym element ColumnName jest nazwa atrybutu i zawartości kolumny są zapisywane jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="15e90-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="15e90-145">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="15e90-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="15e90-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="15e90-146">**SimpleContent**</span></span>|<span data-ttu-id="15e90-147">Zawartość kolumny są zapisywane jako tekst w elemencie XML dla bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="15e90-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="15e90-148">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="15e90-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="15e90-149">Należy pamiętać, że **SimpleContent** nie można ustawić wartości w kolumnie tabeli, która ma **elementu** kolumn lub relacje zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="15e90-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="15e90-150">**Ukryte**</span><span class="sxs-lookup"><span data-stu-id="15e90-150">**Hidden**</span></span>|<span data-ttu-id="15e90-151">Kolumna nie jest zapisywany w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="15e90-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15e90-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15e90-152">See Also</span></span>  
 [<span data-ttu-id="15e90-153">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="15e90-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="15e90-154">Elementy DiffGram</span><span class="sxs-lookup"><span data-stu-id="15e90-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="15e90-155">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="15e90-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="15e90-156">Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD</span><span class="sxs-lookup"><span data-stu-id="15e90-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [<span data-ttu-id="15e90-157">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="15e90-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="15e90-158">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="15e90-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
