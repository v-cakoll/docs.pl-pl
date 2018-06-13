---
title: Ładowanie informacji o schemacie zestawu danych z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760248"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="b2687-102">Ładowanie informacji o schemacie zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="b2687-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="b2687-103">Schemat <xref:System.Data.DataSet> (jego tabele, kolumny, relacji i ograniczeń) mogą być definiowane programowo, utworzone przez **wypełnienia** lub **FillSchema** metody <xref:System.Data.Common.DataAdapter>, lub załadowane z Dokument XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="b2687-104">Aby załadować **zestawu danych** informacji o schemacie z dokumentu XML możesz użyć dowolnej **ReadXmlSchema** lub **InferXmlSchema** metody **zestawudanych**.</span><span class="sxs-lookup"><span data-stu-id="b2687-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b2687-105">**ReadXmlSchema** umożliwia ładowanie lub wnioskować **DataSet** informacji schematu z dokumentu zawierającego schematu (XSD) języka definicji schematu XML lub dokument XML z wbudowanego schematu XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="b2687-106">**InferXmlSchema** pozwala na wnioskowanie schematu z dokumentu XML podczas ignorowanie określonych przestrzeni nazw XML, który określisz.</span><span class="sxs-lookup"><span data-stu-id="b2687-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2687-107">Określanie kolejności w tabeli **DataSet** nie mogą zostać zachowane, korzystając z usług sieci Web lub serializacji XML do transferu **zestawu danych** utworzony w pamięci przy użyciu konstrukcji XSD (na przykład relacjach zagnieżdżonych).</span><span class="sxs-lookup"><span data-stu-id="b2687-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="b2687-108">W związku z tym odbiorcy **DataSet** powinien niezależnie od tabeli w takim przypadku porządkowania.</span><span class="sxs-lookup"><span data-stu-id="b2687-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="b2687-109">Jednak tabeli porządkowania jest zawsze zachowywany, jeśli schemat **zestawu danych** przesyłania zostały odczytane z plików XSD, zamiast tworzona w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b2687-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="b2687-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="b2687-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="b2687-111">Można załadować schematu **DataSet** z dokumentu XML bez ładowania danych, możesz użyć **ReadXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="b2687-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b2687-112">**ReadXmlSchema** tworzy **DataSet** schematu zdefiniowane przy użyciu schematu (XSD) języka definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="b2687-113">**ReadXmlSchema** metoda przyjmuje jeden argument nazwy pliku, typu stream, lub **XmlReader** zawierający można załadować dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="b2687-114">Dokument XML może zawierać tylko schematu lub mogą zawierać wbudowanego schematu z elementów XML z danymi.</span><span class="sxs-lookup"><span data-stu-id="b2687-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="b2687-115">Aby uzyskać informacje na temat pisania wbudowanego schematu XML Schema, zobacz [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="b2687-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="b2687-116">Jeśli dokument XML przekazany do **ReadXmlSchema** nie zawiera żadnych informacji schemat wbudowany **ReadXmlSchema** wywnioskuje schematu z elementów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="b2687-117">Jeśli **DataSet** już zawiera schemat, bieżący schemat zostanie rozszerzony, dodając nowe tabele, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b2687-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="b2687-118">Nowe kolumny nie zostanie dodany do dodane do istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="b2687-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="b2687-119">Jeśli kolumna dodawany już istnieje w **DataSet** , ale ma niezgodny typ z kolumną znaleziony w pliku XML, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b2687-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="b2687-120">Aby uzyskać szczegółowe informacje o tym, jak **ReadXmlSchema** wnioskuje schemat dokumentu XML, zobacz temat [wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b2687-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="b2687-121">Mimo że **ReadXmlSchema** ładuje lub wnioskuje schemat z **DataSet**, **ReadXml** metody **DataSet** ładuje lub wnioskuje zarówno schemat i dane zawarte w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b2687-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="b2687-122">Aby uzyskać więcej informacji, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b2687-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="b2687-123">W poniższych przykładach kodu przedstawiają sposób załadować **DataSet** schematu z dokumentu XML lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="b2687-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="b2687-124">W pierwszym przykładzie pokazano, nazwa pliku schematu XML przekazywany do **ReadXmlSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="b2687-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="b2687-125">W drugim przykładzie **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="b2687-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="b2687-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="b2687-126">InferXmlSchema</span></span>  
 <span data-ttu-id="b2687-127">Można także skonfigurować **DataSet** do wywnioskowany jego schemat dokumentu XML przy użyciu **InferXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="b2687-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="b2687-128">**InferXmlSchema** działa tak samo, jak wykonać obie czynności **ReadXml** z **XmlReadMode** z **InferSchema** (ładuje dane jak również wnioskuje schemat), a **ReadXmlSchema** Jeśli odczytu dokumentu zawiera nie wbudowany schemat.</span><span class="sxs-lookup"><span data-stu-id="b2687-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="b2687-129">Jednak **InferXmlSchema** zapewnia dodatkowe możliwości pozwala określić określonej przestrzeni nazw XML ma być ignorowane podczas jest wywnioskowany schemat.</span><span class="sxs-lookup"><span data-stu-id="b2687-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="b2687-130">**InferXmlSchema** przyjmuje dwa argumenty wymagane: Lokalizacja dokumentu w formacie XML, określony przez nazwę pliku, typu stream, lub **XmlReader**; i przestrzeni nazw XML mają być ignorowane przez operację tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="b2687-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="b2687-131">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="b2687-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="b2687-132">Z powodu atrybutów określonych dla elementów w poprzednim dokument XML zarówno **ReadXmlSchema** — metoda i **ReadXml** metody z **XmlReadMode** z **InferSchema** utworzyć tabele dla każdego elementu w dokumencie: **kategorii**, **CategoryID**, **CategoryName**, **Opis**, **produktów**, **ProductID**, **ReorderLevel**, i **zaprzestać**.</span><span class="sxs-lookup"><span data-stu-id="b2687-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="b2687-133">(Aby uzyskać więcej informacji, zobacz [wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Jednak bardziej odpowiednie struktury będzie można utworzyć tylko **kategorii** i **produktów** tabel, a następnie utworzyć **CategoryID**, **CategoryName** , i **opis** kolumn w **kategorii** tabeli, i **ProductID**, **ReorderLevel**, i **Wycofany** kolumn w **produktów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="b2687-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="b2687-134">Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementów XML, użyj **InferXmlSchema** metodę i określić przestrzeń nazw XML dla **officedata** mają być ignorowane, jak pokazano w Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="b2687-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2687-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2687-135">See Also</span></span>  
 [<span data-ttu-id="b2687-136">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="b2687-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="b2687-137">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b2687-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="b2687-138">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="b2687-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="b2687-139">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="b2687-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="b2687-140">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="b2687-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b2687-141">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b2687-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
