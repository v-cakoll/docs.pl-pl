---
title: Zapisywanie zawartości elementu DataSet jako danych XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: bf73adff89ca5cad3a71239421ac826105a387cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785220"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="09e14-102">Zapisywanie zawartości elementu DataSet jako danych XML</span><span class="sxs-lookup"><span data-stu-id="09e14-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="09e14-103">W ADO.NET można napisać reprezentację <xref:System.Data.DataSet>XML obiektu, z lub bez jego schematu.</span><span class="sxs-lookup"><span data-stu-id="09e14-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="09e14-104">Jeśli informacje o schemacie są dołączone do kodu XML, są zapisywane przy użyciu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="09e14-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="09e14-105">Schemat zawiera definicje <xref:System.Data.DataSet> tabeli, a także relacje i definicje ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="09e14-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="09e14-106">Gdy obiekt <xref:System.Data.DataSet> jest zapisywana jako dane XML, wiersze <xref:System.Data.DataSet> w programie są zapisywane w ich bieżących wersjach.</span><span class="sxs-lookup"><span data-stu-id="09e14-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="09e14-107"><xref:System.Data.DataSet> Jednak może być również zapisany jako DiffGram, tak aby wszystkie bieżące i oryginalne wartości wierszy były uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="09e14-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="09e14-108">Reprezentacja <xref:System.Data.DataSet> XML można zapisać do pliku, strumienia, elementu **XmlWriter**lub ciągu.</span><span class="sxs-lookup"><span data-stu-id="09e14-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="09e14-109">Te opcje zapewniają dużą elastyczność w zakresie transportu reprezentacji <xref:System.Data.DataSet>XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="09e14-110">Aby uzyskać reprezentację <xref:System.Data.DataSet> XML jako ciąg, użyj metody **GetXml —** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09e14-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="09e14-111">**GetXml —** zwraca reprezentację <xref:System.Data.DataSet> XML bez informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="09e14-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="09e14-112">Aby zapisać informacje o schemacie z <xref:System.Data.DataSet> (jako schemat XML) w ciągu, użyj elementu **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="09e14-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="09e14-113">Aby napisać <xref:System.Data.DataSet> plik, strumień lub **XmlWriter**, użyj metody **WriteXml** .</span><span class="sxs-lookup"><span data-stu-id="09e14-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="09e14-114">Pierwszym parametrem przekazywanym do **WriteXml** jest miejsce docelowe danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="09e14-115">Na przykład Przekaż ciąg zawierający nazwę pliku, obiekt **System. IO. TextWriter** i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="09e14-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="09e14-116">Aby określić sposób zapisywania danych wyjściowych XML, można przekazać opcjonalny drugi parametr **XmlWriteMode** .</span><span class="sxs-lookup"><span data-stu-id="09e14-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="09e14-117">W poniższej tabeli przedstawiono opcje elementu **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="09e14-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="09e14-118">XmlWriteMode — opcja</span><span class="sxs-lookup"><span data-stu-id="09e14-118">XmlWriteMode option</span></span>|<span data-ttu-id="09e14-119">Opis</span><span class="sxs-lookup"><span data-stu-id="09e14-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="09e14-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="09e14-120">**IgnoreSchema**</span></span>|<span data-ttu-id="09e14-121">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML, bez schematu XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="09e14-122">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="09e14-122">This is the default.</span></span>|  
|<span data-ttu-id="09e14-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="09e14-123">**WriteSchema**</span></span>|<span data-ttu-id="09e14-124">Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML przy użyciu struktury relacyjnej jako wbudowanego schematu XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="09e14-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="09e14-125">**DiffGram**</span></span>|<span data-ttu-id="09e14-126">Zapisuje cały <xref:System.Data.DataSet> element w formacie DiffGram, w tym pierwotne i bieżące wartości.</span><span class="sxs-lookup"><span data-stu-id="09e14-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="09e14-127">Aby uzyskać więcej informacji, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="09e14-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="09e14-128">Gdy piszesz reprezentację <xref:System.Data.DataSet> **XML zawierającą obiekty** , najprawdopodobniej chcesz, aby otrzymany kod XML miał wszystkie wiersze podrzędne każdej relacji zagnieżdżonej w pokrewnych elementach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="09e14-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="09e14-129">Aby to osiągnąć, należy ustawić **Właściwość zagnieżdżoną** elementu na **wartość true** , gdy dodasz **relację** do <xref:System.Data.DataSet>obiektu.</span><span class="sxs-lookup"><span data-stu-id="09e14-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="09e14-130">Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.</span><span class="sxs-lookup"><span data-stu-id="09e14-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="09e14-131">Poniżej przedstawiono dwa przykłady sposobu pisania reprezentacji <xref:System.Data.DataSet> XML do pliku.</span><span class="sxs-lookup"><span data-stu-id="09e14-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="09e14-132">Pierwszy przykład przekazuje nazwę pliku XML w postaci ciągu do **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="09e14-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="09e14-133">Drugi przykład przekazuje obiekt **System. IO. StreamWriter —** .</span><span class="sxs-lookup"><span data-stu-id="09e14-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="09e14-134">Mapowanie kolumn do elementów XML, atrybutów i tekstu</span><span class="sxs-lookup"><span data-stu-id="09e14-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="09e14-135">Można określić sposób, w jaki kolumna tabeli jest reprezentowana w kodzie XML przy użyciu właściwości **ColumnMapping** obiektu **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="09e14-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="09e14-136">W poniższej tabeli przedstawiono różne wartości **mapowaniatype** dla właściwości **ColumnMapping** kolumny tabeli oraz otrzymany kod XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="09e14-137">Wartość MappingType</span><span class="sxs-lookup"><span data-stu-id="09e14-137">MappingType value</span></span>|<span data-ttu-id="09e14-138">Opis</span><span class="sxs-lookup"><span data-stu-id="09e14-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="09e14-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="09e14-139">**Element**</span></span>|<span data-ttu-id="09e14-140">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="09e14-140">This is the default.</span></span> <span data-ttu-id="09e14-141">Kolumna jest zapisywana jako element XML, gdzie ColumnName jest nazwą elementu, a zawartość kolumny jest zapisywana jako tekst elementu.</span><span class="sxs-lookup"><span data-stu-id="09e14-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="09e14-142">Przykład:</span><span class="sxs-lookup"><span data-stu-id="09e14-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="09e14-143">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="09e14-143">**Attribute**</span></span>|<span data-ttu-id="09e14-144">Kolumna jest zapisywana jako atrybut XML elementu XML dla bieżącego wiersza, gdzie ColumnName jest nazwą atrybutu, a zawartość kolumny jest zapisywana jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09e14-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="09e14-145">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="09e14-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="09e14-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="09e14-146">**SimpleContent**</span></span>|<span data-ttu-id="09e14-147">Zawartość kolumny jest zapisywana jako tekst w elemencie XML dla bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="09e14-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="09e14-148">Przykład:</span><span class="sxs-lookup"><span data-stu-id="09e14-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="09e14-149">Należy zauważyć, że nie można ustawić elementu **SimpleContent** dla kolumny tabeli, która zawiera kolumny **elementów** lub relacje zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="09e14-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="09e14-150">**Ukryte**</span><span class="sxs-lookup"><span data-stu-id="09e14-150">**Hidden**</span></span>|<span data-ttu-id="09e14-151">Kolumna nie jest zapisywana w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="09e14-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09e14-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09e14-152">See also</span></span>

- [<span data-ttu-id="09e14-153">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="09e14-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="09e14-154">Elementy DiffGram</span><span class="sxs-lookup"><span data-stu-id="09e14-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="09e14-155">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="09e14-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="09e14-156">Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD</span><span class="sxs-lookup"><span data-stu-id="09e14-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="09e14-157">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="09e14-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="09e14-158">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09e14-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
