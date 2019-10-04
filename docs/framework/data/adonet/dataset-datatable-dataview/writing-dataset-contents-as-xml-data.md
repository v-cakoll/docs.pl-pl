---
title: Zapisywanie zawartości elementu DataSet jako danych XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833966"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="357c3-102">Zapisywanie zawartości elementu DataSet jako danych XML</span><span class="sxs-lookup"><span data-stu-id="357c3-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="357c3-103">W ADO.NET można napisać reprezentację XML <xref:System.Data.DataSet>, z lub bez jej schematu.</span><span class="sxs-lookup"><span data-stu-id="357c3-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="357c3-104">Jeśli informacje o schemacie są dołączone do kodu XML, są zapisywane przy użyciu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="357c3-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="357c3-105">Schemat zawiera definicje tabeli <xref:System.Data.DataSet> oraz definicje relacji i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="357c3-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="357c3-106">Gdy <xref:System.Data.DataSet> jest zapisywana jako dane XML, wiersze w <xref:System.Data.DataSet> są zapisywane w ich bieżących wersjach.</span><span class="sxs-lookup"><span data-stu-id="357c3-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="357c3-107">Jednak <xref:System.Data.DataSet> może być również zapisany w formacie DiffGram, aby można było uwzględnić zarówno bieżącą, jak i pierwotną wartość wierszy.</span><span class="sxs-lookup"><span data-stu-id="357c3-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="357c3-108">Reprezentacja XML <xref:System.Data.DataSet> może być zapisywana w pliku, strumieniu, elemencie **XmlWriter**lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="357c3-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="357c3-109">Te opcje zapewniają dużą elastyczność w zakresie transportu reprezentację XML <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="357c3-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="357c3-110">Aby uzyskać reprezentację XML <xref:System.Data.DataSet> jako ciąg, użyj metody **GetXml —** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="357c3-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="357c3-111">**GetXml —** zwraca reprezentację XML <xref:System.Data.DataSet> bez informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="357c3-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="357c3-112">Aby zapisać informacje o schemacie z <xref:System.Data.DataSet> (jako schemat XML) do ciągu, użyj elementu **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="357c3-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="357c3-113">Aby napisać <xref:System.Data.DataSet> do pliku, strumienia lub **XmlWriter**, użyj metody **WriteXml** .</span><span class="sxs-lookup"><span data-stu-id="357c3-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="357c3-114">Pierwszym parametrem przekazywanym do **WriteXml** jest miejsce docelowe danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="357c3-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="357c3-115">Na przykład Przekaż ciąg zawierający nazwę pliku, obiekt **System. IO. TextWriter** i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="357c3-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="357c3-116">Aby określić sposób zapisywania danych wyjściowych XML, można przekazać opcjonalny drugi parametr **XmlWriteMode** .</span><span class="sxs-lookup"><span data-stu-id="357c3-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="357c3-117">W poniższej tabeli przedstawiono opcje elementu **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="357c3-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="357c3-118">XmlWriteMode — opcja</span><span class="sxs-lookup"><span data-stu-id="357c3-118">XmlWriteMode option</span></span>|<span data-ttu-id="357c3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="357c3-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="357c3-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="357c3-120">**IgnoreSchema**</span></span>|<span data-ttu-id="357c3-121">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML, bez schematu XML.</span><span class="sxs-lookup"><span data-stu-id="357c3-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="357c3-122">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="357c3-122">This is the default.</span></span>|  
|<span data-ttu-id="357c3-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="357c3-123">**WriteSchema**</span></span>|<span data-ttu-id="357c3-124">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML przy użyciu struktury relacyjnej jako wbudowanego schematu XML.</span><span class="sxs-lookup"><span data-stu-id="357c3-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="357c3-125">**Formacie**</span><span class="sxs-lookup"><span data-stu-id="357c3-125">**DiffGram**</span></span>|<span data-ttu-id="357c3-126">Zapisuje cały <xref:System.Data.DataSet> jako DiffGram, łącznie z oryginalnymi i bieżącymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="357c3-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="357c3-127">Aby uzyskać więcej informacji, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="357c3-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="357c3-128">Podczas pisania reprezentacji XML <xref:System.Data.DataSet>, która **zawiera obiekty** , najprawdopodobniej chcesz, aby otrzymany kod XML miał wszystkie wiersze podrzędne dla każdej relacji zagnieżdżone w pokrewnych elementach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="357c3-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="357c3-129">**Aby to** osiągnąć, należy ustawić właściwość **zagnieżdżoną** elementu na **wartość true** , gdy dodasz **relację** do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="357c3-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="357c3-130">Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.</span><span class="sxs-lookup"><span data-stu-id="357c3-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="357c3-131">Poniżej przedstawiono dwa przykłady sposobu pisania reprezentacji XML <xref:System.Data.DataSet> do pliku.</span><span class="sxs-lookup"><span data-stu-id="357c3-131">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="357c3-132">Pierwszy przykład przekazuje nazwę pliku XML w postaci ciągu do **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="357c3-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="357c3-133">Drugi przykład przekazuje obiekt **System. IO. StreamWriter —** .</span><span class="sxs-lookup"><span data-stu-id="357c3-133">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="357c3-134">Mapowanie kolumn do elementów XML, atrybutów i tekstu</span><span class="sxs-lookup"><span data-stu-id="357c3-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="357c3-135">Można określić sposób, w jaki kolumna tabeli jest reprezentowana w kodzie XML przy użyciu właściwości **ColumnMapping** obiektu **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="357c3-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="357c3-136">W poniższej tabeli przedstawiono różne wartości **mapowaniatype** dla właściwości **ColumnMapping** kolumny tabeli oraz otrzymany kod XML.</span><span class="sxs-lookup"><span data-stu-id="357c3-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="357c3-137">Wartość MappingType</span><span class="sxs-lookup"><span data-stu-id="357c3-137">MappingType value</span></span>|<span data-ttu-id="357c3-138">Opis</span><span class="sxs-lookup"><span data-stu-id="357c3-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="357c3-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="357c3-139">**Element**</span></span>|<span data-ttu-id="357c3-140">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="357c3-140">This is the default.</span></span> <span data-ttu-id="357c3-141">Kolumna jest zapisywana jako element XML, gdzie ColumnName jest nazwą elementu, a zawartość kolumny jest zapisywana jako tekst elementu.</span><span class="sxs-lookup"><span data-stu-id="357c3-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="357c3-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="357c3-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="357c3-143">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="357c3-143">**Attribute**</span></span>|<span data-ttu-id="357c3-144">Kolumna jest zapisywana jako atrybut XML elementu XML dla bieżącego wiersza, gdzie ColumnName jest nazwą atrybutu, a zawartość kolumny jest zapisywana jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="357c3-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="357c3-145">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="357c3-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="357c3-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="357c3-146">**SimpleContent**</span></span>|<span data-ttu-id="357c3-147">Zawartość kolumny jest zapisywana jako tekst w elemencie XML dla bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="357c3-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="357c3-148">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="357c3-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="357c3-149">Należy zauważyć, że nie można ustawić elementu **SimpleContent** dla kolumny tabeli, która zawiera kolumny **elementów** lub relacje zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="357c3-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="357c3-150">**Ukryte**</span><span class="sxs-lookup"><span data-stu-id="357c3-150">**Hidden**</span></span>|<span data-ttu-id="357c3-151">Kolumna nie jest zapisywana w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="357c3-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="357c3-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="357c3-152">See also</span></span>

- [<span data-ttu-id="357c3-153">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="357c3-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="357c3-154">Elementy DiffGram</span><span class="sxs-lookup"><span data-stu-id="357c3-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="357c3-155">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="357c3-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="357c3-156">Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD</span><span class="sxs-lookup"><span data-stu-id="357c3-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="357c3-157">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="357c3-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="357c3-158">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="357c3-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
