---
title: Ładowanie informacji o schemacie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151055"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="7142c-102">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7142c-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="7142c-103">Schemat <xref:System.Data.DataSet> (jego tabele, kolumny, relacje i ograniczenia) można zdefiniować programowo, utworzony przez **metody Wypełnij** lub **FillSchema** <xref:System.Data.Common.DataAdapter>, lub załadowany z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="7142c-104">Aby załadować informacje o schemacie **Zestawu danych** z dokumentu XML, można użyć metody **ReadXmlSchema** lub **InferXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7142c-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7142c-105">**ReadXmlSchema** umożliwia ładowanie lub wnioskowanie informacji o schemacie **zestawu danych** z dokumentu zawierającego schemat języka XSD (XSD) lub dokumentu XML ze schematem XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="7142c-106">**InferXmlSchema** umożliwia wywnioskowanie schematu z dokumentu XML, ignorując niektóre określone przestrzenie nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7142c-107">Kolejność tabel w **zestawie danych** może nie zostać zachowana podczas przesyłania zestawu **danych** utworzonego w pamięci przy użyciu konstrukcji XSD (takich jak relacje zagnieżdżone) za pomocą usług sieci Web lub serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="7142c-108">W związku z tym odbiorca **DataSet** nie powinny zależeć od kolejności tabeli w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="7142c-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="7142c-109">Jednak kolejność tabel jest zawsze zachowywana, jeśli schemat zestawu **danych, który** jest przesyłany, został odczytany z plików XSD, a nie został utworzony w pamięci.</span><span class="sxs-lookup"><span data-stu-id="7142c-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="7142c-110">Readxmlschema</span><span class="sxs-lookup"><span data-stu-id="7142c-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="7142c-111">Aby załadować schemat **zestawu danych** z dokumentu XML bez ładowania żadnych danych, można użyć metody **ReadXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7142c-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7142c-112">**ReadXmlSchema** tworzy schemat **DataSet** zdefiniowany przy użyciu schematu języka XM (XSD) języka schematu XMD.</span><span class="sxs-lookup"><span data-stu-id="7142c-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="7142c-113">Metoda **ReadXmlSchema** przyjmuje pojedynczy argument nazwy pliku, strumienia lub **czytnika XmlReader** zawierającego dokument XML do załadowania.</span><span class="sxs-lookup"><span data-stu-id="7142c-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="7142c-114">Dokument XML może zawierać tylko schemat lub może zawierać schemat wyklinowy z elementami XML zawierającymi dane.</span><span class="sxs-lookup"><span data-stu-id="7142c-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="7142c-115">Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [Wyprowadzanie struktury relacyjnej zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7142c-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="7142c-116">Jeśli dokument XML przekazany do **ReadXmlSchema** nie zawiera żadnych wbudowanych informacji o schemacie, **program ReadXmlSchema** wywnioskuje schemat z elementów dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="7142c-117">Jeśli **Zestaw danych** zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie nowych tabel, jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="7142c-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="7142c-118">Nowe kolumny nie zostaną dodane do istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="7142c-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="7142c-119">Jeśli dodawana kolumna już istnieje w **zestawie danych,** ale ma niezgodny typ z kolumną znalezioną w pliku XML, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7142c-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="7142c-120">Aby uzyskać szczegółowe informacje o tym, jak **program ReadXmlSchema** wylicza schemat z dokumentu XML, zobacz [Wnioskowanie struktury relacyjnej zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7142c-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="7142c-121">Chociaż **ReadXmlSchema** ładuje lub wywnioskować tylko schemat **zestawu danych,** metoda **ReadXml** **zestawu danych** ładuje lub wywnioskowała zarówno schemat, jak i dane zawarte w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="7142c-122">Aby uzyskać więcej informacji, zobacz [Ładowanie zestawu danych z pliku XML](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7142c-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="7142c-123">Poniższe przykłady kodu pokazują, jak załadować schemat **zestawu danych** z dokumentu lub strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="7142c-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="7142c-124">W pierwszym przykładzie przedstawiono nazwę pliku schematu XML przekazywany do metody **ReadXmlSchema.**</span><span class="sxs-lookup"><span data-stu-id="7142c-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="7142c-125">Drugi przykład pokazuje **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="7142c-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="7142c-126">Inferxmlschema</span><span class="sxs-lookup"><span data-stu-id="7142c-126">InferXmlSchema</span></span>  
 <span data-ttu-id="7142c-127">Można również poinstruować **zestaw danych,** aby wywnioskować jego schemat z dokumentu XML przy użyciu metody **InferXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7142c-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7142c-128">**InferXmlSchema** działa tak samo, jak zarówno **ReadXml** z **XmlReadMode** **inferSchema** (ładuje dane, jak również schemat wnioskujący), jak i **ReadXmlSchema,** jeśli odczytywany dokument nie zawiera schematu wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="7142c-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="7142c-129">Jednak **InferXmlSchema** zapewnia dodatkową możliwość umożliwiając określenie określonych obszarów nazw XML, które mają być ignorowane, gdy schemat jest wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="7142c-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="7142c-130">**InferXmlSchema** przyjmuje dwa wymagane argumenty: lokalizację dokumentu XML, określoną przez nazwę pliku, strumień lub **XmlReader;** oraz tablicę ciągów obszarów nazw XML, które mają być ignorowane przez operację.</span><span class="sxs-lookup"><span data-stu-id="7142c-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="7142c-131">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="7142c-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="7142c-132">Ze względu na atrybuty określone dla elementów w poprzednim dokumencie XML zarówno **ReadXmlSchema,** jak i **Metoda ReadXml** z **XmlReadMode** **of InferSchema** utworzą tabele dla każdego elementu w dokumencie: **Kategorie**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**i **Discontinued**.</span><span class="sxs-lookup"><span data-stu-id="7142c-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="7142c-133">(Aby uzyskać więcej informacji, zobacz [Wywnioskowanie struktury relacyjnej zestawu danych z XML).](inferring-dataset-relational-structure-from-xml.md) Jednak bardziej odpowiednią strukturą byłoby utworzenie tylko tabel **Kategorie** i **Produkty,** a następnie utworzenie kolumn **CategoryID**, **CategoryName**i **Description** w tabeli **Kategorie** oraz **ProductID**, **ReorderLevel**i **Wycofane** kolumny w tabeli **Produkty.**</span><span class="sxs-lookup"><span data-stu-id="7142c-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="7142c-134">Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementach XML, użyj metody **InferXmlSchema** i określ obszar nazw XML dla **danych biurowych,** które mają być ignorowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7142c-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7142c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7142c-135">See also</span></span>

- [<span data-ttu-id="7142c-136">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="7142c-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="7142c-137">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7142c-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7142c-138">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7142c-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7142c-139">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7142c-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="7142c-140">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7142c-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7142c-141">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7142c-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
