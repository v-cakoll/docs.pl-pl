---
title: Ładowanie informacji o schemacie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: db0df68aa89cdd5c8bf94ad95a2b8bc9b36d5685
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786219"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="7ab40-102">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7ab40-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="7ab40-103">Schemat <xref:System.Data.DataSet> (tabele, kolumny, relacje i ograniczenia) można definiować programowo, tworząc przy użyciu metod <xref:System.Data.Common.DataAdapter> **Fill** lub **FillSchema** lub załadowanych z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="7ab40-104">Aby załadować informacje o schemacie **zestawu danych** z dokumentu XML, można użyć metody **ReadXmlSchema** lub **InferXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7ab40-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7ab40-105">**ReadXmlSchema** umożliwia ładowanie lub wnioskowanie informacji o schemacie **zestawu danych** z dokumentu zawierającego schemat języka definicji schematu XML (XSD) lub dokument XML z wbudowanym schematem XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="7ab40-106">**InferXmlSchema** umożliwia wywnioskowanie schematu z dokumentu XML podczas ignorowania określonych przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ab40-107">Porządkowanie tabeli w **zestawie danych** może nie być zachowywane podczas korzystania z usług sieci Web lub serializacji XML do transferu **zestawu danych** , który został utworzony w pamięci przy użyciu konstrukcji XSD (takich jak relacje zagnieżdżone).</span><span class="sxs-lookup"><span data-stu-id="7ab40-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="7ab40-108">W związku z tym odbiorca **zestawu danych** nie powinien zależeć od uporządkowania tabeli w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="7ab40-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="7ab40-109">Jednak porządkowanie tabeli jest zawsze zachowywane, jeśli schemat transferu **danych** został odczytany z plików XSD, zamiast tworzyć w pamięci.</span><span class="sxs-lookup"><span data-stu-id="7ab40-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="7ab40-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7ab40-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="7ab40-111">Aby załadować schemat **zestawu danych** z dokumentu XML bez ładowania jakichkolwiek danych, można użyć metody **ReadXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7ab40-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7ab40-112">**ReadXmlSchema** tworzy schemat **zestawu danych** zdefiniowany przy użyciu schematu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="7ab40-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="7ab40-113">Metoda **ReadXmlSchema** przyjmuje pojedynczy argument nazwy pliku, strumienia lub elementu **XMLREADER** zawierającego dokument XML do załadowania.</span><span class="sxs-lookup"><span data-stu-id="7ab40-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="7ab40-114">Dokument XML może zawierać tylko schemat lub może zawierać schemat w tekście z elementami XML zawierającymi dane.</span><span class="sxs-lookup"><span data-stu-id="7ab40-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="7ab40-115">Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7ab40-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="7ab40-116">Jeśli dokument XML przesłany do **ReadXmlSchema** nie zawiera wbudowanych informacji o schemacie, **ReadXmlSchema** będzie wnioskować o schemat z elementów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="7ab40-117">Jeśli **zestaw danych** zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie nowych tabel, jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="7ab40-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="7ab40-118">Nowe kolumny nie zostaną dodane do istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="7ab40-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="7ab40-119">Jeśli dodawana kolumna już istnieje w **zestawie danych** , ale ma niezgodny typ z kolumną znalezioną w kodzie XML, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7ab40-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="7ab40-120">Aby uzyskać szczegółowe informacje na temat sposobu, w jaki program **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz [wnioskowanie o relacyjnej strukturze zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7ab40-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="7ab40-121">Mimo że **ReadXmlSchema** ładuje lub wnioskuje tylko schemat **zestawu danych**, Metoda **ReadXml** **zestawu danych** ładuje lub wnioskuje schemat oraz dane zawarte w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="7ab40-122">Aby uzyskać więcej informacji, zobacz [Ładowanie zestawu danych z pliku XML](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7ab40-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="7ab40-123">Poniższy przykład kodu pokazuje, jak załadować schemat **zestawu danych** z dokumentu lub strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="7ab40-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="7ab40-124">Pierwszy przykład przedstawia nazwę pliku schematu XML, który jest przesyłany do metody **ReadXmlSchema** .</span><span class="sxs-lookup"><span data-stu-id="7ab40-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="7ab40-125">W drugim przykładzie pokazano element **System. IO. StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="7ab40-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="7ab40-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7ab40-126">InferXmlSchema</span></span>  
 <span data-ttu-id="7ab40-127">Można również nakazać **zestawowi danych** wywnioskowanie schematu z dokumentu XML przy użyciu metody **InferXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="7ab40-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7ab40-128">Funkcja **InferXmlSchema** działa tak samo jak w przypadku obu **ReadXml** z atrybutem **XmlReadMode** of **InferSchema** (ładuje dane, a także schemat wniosku) i **ReadXmlSchema** , jeśli dokument jest odczytywany nie zawiera wbudowanego schematu.</span><span class="sxs-lookup"><span data-stu-id="7ab40-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="7ab40-129">**InferXmlSchema** oferuje jednak dodatkową możliwość, która umożliwia określenie określonych przestrzeni nazw XML, które mają być ignorowane, gdy schemat zostanie wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="7ab40-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="7ab40-130">**InferXmlSchema** przyjmuje dwa wymagane argumenty: lokalizację dokumentu XML, określoną przez nazwę pliku, strumień lub element **XmlReader**; i tablica ciągów przestrzeni nazw XML, która ma być ignorowana przez operację.</span><span class="sxs-lookup"><span data-stu-id="7ab40-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="7ab40-131">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="7ab40-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="7ab40-132">Ze względu na atrybuty określone dla elementów w poprzednim dokumencie XML, Metoda **ReadXmlSchema** i Metoda **ReadXml** z atrybutem **XmlReadMode** klasy **InferSchema** utworzy tabele dla każdego elementu w dokumentu **Kategorie**, **IDkategorii**, **CategoryName**, **Opis**, **produkty**, **ProductID**, **ReorderLevel**i **wycofane**.</span><span class="sxs-lookup"><span data-stu-id="7ab40-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="7ab40-133">(Aby uzyskać więcej informacji, zobacz [wnioskowanie relacyjnej struktury zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md)). Jednak bardziej odpowiednią strukturą jest utworzenie tylko tabel **Kategorie** i **produkty** , a następnie utworzenie kolumn **IDkategorii**, **CategoryName**i **Description** w tabeli **Kategorie** i  **Kolumny ProductID**, **ReorderLevel**i **uncontinued** w tabeli **Products** .</span><span class="sxs-lookup"><span data-stu-id="7ab40-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="7ab40-134">Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementach XML, należy użyć metody **InferXmlSchema** i określić przestrzeń nazw **XML do** ignorowania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7ab40-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ab40-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ab40-135">See also</span></span>

- [<span data-ttu-id="7ab40-136">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="7ab40-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="7ab40-137">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7ab40-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7ab40-138">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7ab40-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7ab40-139">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="7ab40-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="7ab40-140">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7ab40-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7ab40-141">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7ab40-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
