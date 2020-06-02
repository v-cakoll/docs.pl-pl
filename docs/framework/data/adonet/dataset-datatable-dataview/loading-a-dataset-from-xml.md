---
title: Ładowanie elementu DataSet z pliku XML
description: Dowiedz się, jak dodać zawartość do zestawu danych ADO.NET z pliku XML. .NET Framework oferuje elastyczność do obciążenia i struktury zestawu danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 8c81e6e29678fe2e30af7c15d8d6e90f23dd0762
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286886"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="43f94-104">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="43f94-104">Loading a DataSet from XML</span></span>
<span data-ttu-id="43f94-105">Zawartość ADO.NET <xref:System.Data.DataSet> można utworzyć na podstawie strumienia lub dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="43f94-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="43f94-106">Ponadto dzięki .NET Framework masz doskonałą elastyczność nad tym, jakie informacje są ładowane z pliku XML, oraz sposób tworzenia schematu lub struktury relacyjnej <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="43f94-107">Aby wypełnić <xref:System.Data.DataSet> danymi z XML, użyj metody **ReadXml** <xref:System.Data.DataSet> obiektu.</span><span class="sxs-lookup"><span data-stu-id="43f94-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="43f94-108">Metoda **ReadXml** odczytuje z pliku, strumienia lub elementu **XmlReader**i przyjmuje jako argumenty Źródło XML i opcjonalny argument **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="43f94-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="43f94-109">Aby uzyskać więcej informacji na temat elementu **XmlReader**, zobacz [odczytywanie danych XML za pomocą XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="43f94-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="43f94-110">Metoda **ReadXml** odczytuje zawartość strumienia XML lub dokumentu i ładuje <xref:System.Data.DataSet> dane z danymi.</span><span class="sxs-lookup"><span data-stu-id="43f94-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="43f94-111">Zostanie również utworzony schemat relacyjny w <xref:System.Data.DataSet> zależności od typu **XmlReadMode** oraz tego, czy schemat relacyjny już istnieje.</span><span class="sxs-lookup"><span data-stu-id="43f94-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="43f94-112">W poniższej tabeli opisano opcje dla argumentu **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="43f94-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="43f94-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="43f94-113">Option</span></span>|<span data-ttu-id="43f94-114">Opis</span><span class="sxs-lookup"><span data-stu-id="43f94-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="43f94-115">**Automatycznie**</span><span class="sxs-lookup"><span data-stu-id="43f94-115">**Auto**</span></span>|<span data-ttu-id="43f94-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="43f94-116">This is the default.</span></span> <span data-ttu-id="43f94-117">Bada kod XML i wybiera najbardziej odpowiednią opcję w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="43f94-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="43f94-118">-Jeśli plik XML jest w formacie DiffGram, jest używany element **DiffGram** .</span><span class="sxs-lookup"><span data-stu-id="43f94-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="43f94-119">-Jeśli <xref:System.Data.DataSet> zawiera schemat lub XML zawiera schemat wbudowany, **ReadSchema** jest używany.</span><span class="sxs-lookup"><span data-stu-id="43f94-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="43f94-120">-Jeśli nie <xref:System.Data.DataSet> zawiera schematu, a XML nie zawiera wbudowanego schematu, **InferSchema** jest używany.</span><span class="sxs-lookup"><span data-stu-id="43f94-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="43f94-121">Jeśli znasz format odczytywanego kodu XML, w celu uzyskania najlepszej wydajności zaleca się ustawienie jawnego elementu **XmlReadMode**, a nie akceptowanie **wartości domyślnej.**</span><span class="sxs-lookup"><span data-stu-id="43f94-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="43f94-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="43f94-122">**ReadSchema**</span></span>|<span data-ttu-id="43f94-123">Odczytuje wszystkie wbudowane schematy i ładuje dane i schemat.</span><span class="sxs-lookup"><span data-stu-id="43f94-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="43f94-124">Jeśli <xref:System.Data.DataSet> zawiera już schemat, nowe tabele są dodawane z schematu wbudowanego do istniejącego schematu w programie <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="43f94-125">Wyjątek jest zgłaszany, jeśli dowolna tabela w schemacie wbudowanym już istnieje <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="43f94-126">Nie będzie można modyfikować schematu istniejącej tabeli przy użyciu elementu **XmlReadMode. ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="43f94-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="43f94-127">Jeśli nie <xref:System.Data.DataSet> zawiera schematu i nie ma wbudowanego schematu, żadne dane nie są odczytywane.</span><span class="sxs-lookup"><span data-stu-id="43f94-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="43f94-128">Schemat wbudowany można zdefiniować przy użyciu schematu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="43f94-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="43f94-129">Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="43f94-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="43f94-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="43f94-130">**IgnoreSchema**</span></span>|<span data-ttu-id="43f94-131">Ignoruje wszystkie wbudowane schemat i ładuje dane do istniejącego <xref:System.Data.DataSet> schematu.</span><span class="sxs-lookup"><span data-stu-id="43f94-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="43f94-132">Wszystkie dane, które nie są zgodne z istniejącym schematem, są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="43f94-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="43f94-133">Jeśli żaden schemat nie istnieje w <xref:System.Data.DataSet> , żadne dane nie są ładowane.</span><span class="sxs-lookup"><span data-stu-id="43f94-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="43f94-134">Jeśli dane są w formacie DiffGram, **IgnoreSchema** ma takie same funkcje jak **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="43f94-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="43f94-135">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="43f94-135">**InferSchema**</span></span>|<span data-ttu-id="43f94-136">Ignoruje wszystkie wbudowane schemat i wnioskuje schemat na strukturę danych XML, a następnie ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="43f94-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="43f94-137">Jeśli <xref:System.Data.DataSet> zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie kolumn do istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="43f94-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="43f94-138">Dodatkowe tabele nie zostaną dodane, jeśli nie ma istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="43f94-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="43f94-139">Wyjątek jest zgłaszany, jeśli wywnioskowana tabela już istnieje z inną przestrzenią nazw lub jeśli wszystkie wywnioskowane kolumny kolidują z istniejącymi kolumnami.</span><span class="sxs-lookup"><span data-stu-id="43f94-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="43f94-140">Aby uzyskać szczegółowe informacje na temat sposobu, w jaki program **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz [wnioskowanie o relacyjnej strukturze zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="43f94-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="43f94-141">**Formacie**</span><span class="sxs-lookup"><span data-stu-id="43f94-141">**DiffGram**</span></span>|<span data-ttu-id="43f94-142">Odczytuje element DiffGram i dodaje dane do bieżącego schematu.</span><span class="sxs-lookup"><span data-stu-id="43f94-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="43f94-143">Format **DiffGram** Scala nowe wiersze z istniejącymi wierszami, w których unikatowe wartości identyfikatorów są zgodne.</span><span class="sxs-lookup"><span data-stu-id="43f94-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="43f94-144">Zobacz "scalanie danych z pliku XML" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="43f94-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="43f94-145">Aby uzyskać więcej informacji na temat DiffGrams, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="43f94-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="43f94-146">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="43f94-146">**Fragment**</span></span>|<span data-ttu-id="43f94-147">Kontynuuje odczytywanie wielu fragmentów kodu XML do momentu osiągnięcia końca strumienia.</span><span class="sxs-lookup"><span data-stu-id="43f94-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="43f94-148">Fragmenty, które pasują do <xref:System.Data.DataSet> schematu, są dołączane do odpowiednich tabel.</span><span class="sxs-lookup"><span data-stu-id="43f94-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="43f94-149">Fragmenty, które nie pasują do <xref:System.Data.DataSet> schematu, są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="43f94-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="43f94-150">Jeśli przekażesz element **XmlReader** do **ReadXml** , który jest umieszczony częścią sposobu w dokumencie XML, **ReadXml** zostanie odczytany do następnego węzła elementu i będzie traktowany jako element główny, odczytując do końca węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="43f94-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="43f94-151">Nie ma to zastosowania w przypadku określenia **XmlReadMode. fragment**.</span><span class="sxs-lookup"><span data-stu-id="43f94-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="43f94-152">Jednostki DTD</span><span class="sxs-lookup"><span data-stu-id="43f94-152">DTD Entities</span></span>  
 <span data-ttu-id="43f94-153">Jeśli plik XML zawiera jednostki zdefiniowane w schemacie definicji typu dokumentu (DTD), zostanie zgłoszony wyjątek w przypadku próby załadowania <xref:System.Data.DataSet> przez przekazanie pliku o nazwie, strumienia lub braku sprawdzania poprawności elementu **XmlReader** do **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="43f94-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="43f94-154">Zamiast tego należy utworzyć element **XmlValidatingReader**z opcją **EntityHandling** ustawioną na **EntityHandling. ExpandEntities**i przekazać **XmlValidatingReader** do **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="43f94-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="43f94-155">**XmlValidatingReader** rozwinie jednostki przed odczytaniem przez <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="43f94-156">Poniższy przykład kodu przedstawia sposób ładowania <xref:System.Data.DataSet> ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="43f94-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="43f94-157">Pierwszy przykład przedstawia nazwę pliku, który jest przesyłany do metody **ReadXml** .</span><span class="sxs-lookup"><span data-stu-id="43f94-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="43f94-158">W drugim przykładzie przedstawiono ciąg zawierający kod XML, który jest ładowany przy użyciu <xref:System.IO.StringReader> .</span><span class="sxs-lookup"><span data-stu-id="43f94-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="43f94-159">Jeśli wywołasz **ReadXml** do załadowania bardzo dużego pliku, może wystąpić spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="43f94-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="43f94-160">Aby zapewnić najlepszą wydajność dla **ReadXml**, w dużym pliku Wywołaj <xref:System.Data.DataTable.BeginLoadData%2A> metodę dla każdej tabeli w <xref:System.Data.DataSet> , a następnie Wywołaj **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="43f94-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="43f94-161">Na koniec Wywołaj <xref:System.Data.DataTable.EndLoadData%2A> dla każdej tabeli w <xref:System.Data.DataSet> , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="43f94-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="43f94-162">Jeśli schemat XSD dla <xref:System.Data.DataSet> zawiera element **targetNamespace**, dane mogą nie być odczytywane i mogą wystąpić wyjątki, gdy wywołując **ReadXml** do ładowania <xref:System.Data.DataSet> pliku XML, który zawiera elementy bez kwalifikującej się przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43f94-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="43f94-163">Aby odczytywać niekwalifikowane elementy w tym przypadku, ustaw **elementFormDefault** równe "kwalifikowana" w schemacie XSD.</span><span class="sxs-lookup"><span data-stu-id="43f94-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="43f94-164">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="43f94-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="43f94-165">Scalanie danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="43f94-165">Merging Data from XML</span></span>  
 <span data-ttu-id="43f94-166">Jeśli <xref:System.Data.DataSet> zawiera już dane, nowe dane z pliku XML zostaną dodane do danych znajdujących się już w <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="43f94-167">**ReadXml** nie scala danych z pliku XML z <xref:System.Data.DataSet> dowolnymi informacjami o wierszach ze zgodnymi kluczami podstawowymi.</span><span class="sxs-lookup"><span data-stu-id="43f94-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="43f94-168">Aby zastąpić informacje o istniejących wierszach nowymi informacjami z pliku XML, użyj **ReadXml** , aby utworzyć nowe <xref:System.Data.DataSet> , a następnie <xref:System.Data.DataSet.Merge%2A> nowe <xref:System.Data.DataSet> do istniejącej <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="43f94-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="43f94-169">Należy zauważyć, że załadowanie pliku DiffGram przy użyciu **ReadXml** z atrybutem **XmlReadMode** z elementu **DiffGram** spowoduje scalenie wierszy, które mają ten sam unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="43f94-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f94-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43f94-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="43f94-171">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="43f94-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="43f94-172">Elementy DiffGram</span><span class="sxs-lookup"><span data-stu-id="43f94-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="43f94-173">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="43f94-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="43f94-174">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="43f94-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="43f94-175">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="43f94-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="43f94-176">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="43f94-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="43f94-177">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43f94-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
