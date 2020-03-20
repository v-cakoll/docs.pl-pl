---
title: Ładowanie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151068"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="06d5f-102">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="06d5f-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="06d5f-103">Zawartość ADO.NET <xref:System.Data.DataSet> można utworzyć na podstawie strumienia lub dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="06d5f-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="06d5f-104">Ponadto w ramach .NET Framework masz dużą elastyczność w odniesieniu do informacji, które są ładowane z XML i jak tworzony <xref:System.Data.DataSet> jest schemat lub relacyjne struktury.</span><span class="sxs-lookup"><span data-stu-id="06d5f-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="06d5f-105">Aby wypełnić dane <xref:System.Data.DataSet> z XML, użyj metody <xref:System.Data.DataSet> **ReadXml** obiektu.</span><span class="sxs-lookup"><span data-stu-id="06d5f-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="06d5f-106">Metoda **ReadXml** odczytuje z pliku, strumienia lub **XmlReader**i przyjmuje jako argumenty źródło XML oraz opcjonalny argument **XmlReadMode.**</span><span class="sxs-lookup"><span data-stu-id="06d5f-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="06d5f-107">Aby uzyskać więcej informacji na temat **czytnika XmlReader,** zobacz [Odczytywanie danych XML za pomocą czytnika XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="06d5f-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="06d5f-108">Metoda **ReadXml** odczytuje zawartość strumienia lub dokumentu XML i ładuje <xref:System.Data.DataSet> dane.</span><span class="sxs-lookup"><span data-stu-id="06d5f-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="06d5f-109">Spowoduje to również utworzenie schematu <xref:System.Data.DataSet> relacyjnego w zależności od **XmlReadMode** określony i czy schemat relacyjne już istnieje.</span><span class="sxs-lookup"><span data-stu-id="06d5f-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="06d5f-110">W poniższej tabeli opisano opcje argumentu **XmlReadMode.**</span><span class="sxs-lookup"><span data-stu-id="06d5f-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="06d5f-111">Opcja</span><span class="sxs-lookup"><span data-stu-id="06d5f-111">Option</span></span>|<span data-ttu-id="06d5f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="06d5f-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="06d5f-113">**Automatycznie**</span><span class="sxs-lookup"><span data-stu-id="06d5f-113">**Auto**</span></span>|<span data-ttu-id="06d5f-114">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="06d5f-114">This is the default.</span></span> <span data-ttu-id="06d5f-115">Sprawdza kod XML i wybiera najbardziej odpowiednią opcję w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="06d5f-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="06d5f-116">- Jeśli XML jest DiffGram, **DiffGram** jest używany.</span><span class="sxs-lookup"><span data-stu-id="06d5f-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="06d5f-117">- Jeśli <xref:System.Data.DataSet> zawiera schemat lub XML zawiera wbudowany schemat, **ReadSchema** jest używany.</span><span class="sxs-lookup"><span data-stu-id="06d5f-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="06d5f-118">- Jeśli <xref:System.Data.DataSet> nie zawiera schematu i XML nie zawiera schematu wbudowanego, **InferSchema** jest używany.</span><span class="sxs-lookup"><span data-stu-id="06d5f-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="06d5f-119">Jeśli znasz format odczytu pliku XML, aby uzyskać najlepszą wydajność, zaleca się ustawienie jawnego **trybu XmlReadMode**zamiast akceptowania **domyślnego ustawienia automatycznego.**</span><span class="sxs-lookup"><span data-stu-id="06d5f-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="06d5f-120">**ReadSchema ( ReadSchema )**</span><span class="sxs-lookup"><span data-stu-id="06d5f-120">**ReadSchema**</span></span>|<span data-ttu-id="06d5f-121">Odczytuje dowolny schemat wbudowany i ładuje dane i schemat.</span><span class="sxs-lookup"><span data-stu-id="06d5f-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="06d5f-122">Jeśli <xref:System.Data.DataSet> schemat zawiera już schemat, nowe tabele są dodawane ze schematu <xref:System.Data.DataSet>wbudowanego do istniejącego schematu w pliku .</span><span class="sxs-lookup"><span data-stu-id="06d5f-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06d5f-123">Jeśli istnieją już jakieś tabele w <xref:System.Data.DataSet>schemacie wbudowanym w , zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="06d5f-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="06d5f-124">Nie będzie można zmodyfikować schematu istniejącej tabeli za pomocą **pliku XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="06d5f-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="06d5f-125">Jeśli <xref:System.Data.DataSet> nie zawiera schematu i nie ma schematu wbudowanego, nie są odczytywane żadne dane.</span><span class="sxs-lookup"><span data-stu-id="06d5f-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="06d5f-126">Schemat wbudowany można zdefiniować przy użyciu schematu języka XSD (XSD).</span><span class="sxs-lookup"><span data-stu-id="06d5f-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="06d5f-127">Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [Wyprowadzanie struktury relacyjnej zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="06d5f-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="06d5f-128">**IgnoreSchema (Ignorschema)**</span><span class="sxs-lookup"><span data-stu-id="06d5f-128">**IgnoreSchema**</span></span>|<span data-ttu-id="06d5f-129">Ignoruje schemat wbudowany i ładuje dane <xref:System.Data.DataSet> do istniejącego schematu.</span><span class="sxs-lookup"><span data-stu-id="06d5f-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="06d5f-130">Wszystkie dane, które nie pasują do istniejącego schematu jest odrzucany.</span><span class="sxs-lookup"><span data-stu-id="06d5f-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="06d5f-131">Jeśli w pliku , <xref:System.Data.DataSet>nie ma schematu, nie są ładowane żadne dane.</span><span class="sxs-lookup"><span data-stu-id="06d5f-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="06d5f-132">Jeśli dane są DiffGram, **IgnoreSchema** ma taką samą funkcjonalność jak **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="06d5f-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="06d5f-133">**Inferschema**</span><span class="sxs-lookup"><span data-stu-id="06d5f-133">**InferSchema**</span></span>|<span data-ttu-id="06d5f-134">Ignoruje schemat wbudowany i wywnioskować schemat na strukturę danych XML, a następnie ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="06d5f-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="06d5f-135">Jeśli <xref:System.Data.DataSet> już zawiera schemat, bieżący schemat jest rozszerzany przez dodanie kolumn do istniejących tabel.</span><span class="sxs-lookup"><span data-stu-id="06d5f-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="06d5f-136">Dodatkowe tabele nie zostaną dodane, jeśli nie istnieją istniejące tabele.</span><span class="sxs-lookup"><span data-stu-id="06d5f-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="06d5f-137">Wyjątek jest zgłaszany, jeśli wywnioskowana tabela już istnieje z innym obszarem nazw lub jeśli jakieś wywnioskowane kolumny są w konflikcie z istniejącymi kolumnami.</span><span class="sxs-lookup"><span data-stu-id="06d5f-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="06d5f-138">Aby uzyskać szczegółowe informacje o tym, jak **program ReadXmlSchema** wylicza schemat z dokumentu XML, zobacz [Wnioskowanie struktury relacyjnej zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06d5f-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="06d5f-139">**Formacie diffgram**</span><span class="sxs-lookup"><span data-stu-id="06d5f-139">**DiffGram**</span></span>|<span data-ttu-id="06d5f-140">Odczytuje DiffGram i dodaje dane do bieżącego schematu.</span><span class="sxs-lookup"><span data-stu-id="06d5f-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="06d5f-141">**DiffGram** scala nowe wiersze z istniejącymi wierszami, w których są zgodne wartości unikatowych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="06d5f-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="06d5f-142">Zobacz "Scalanie danych z XML" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="06d5f-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="06d5f-143">Aby uzyskać więcej informacji na temat DiffGramów, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="06d5f-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="06d5f-144">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="06d5f-144">**Fragment**</span></span>|<span data-ttu-id="06d5f-145">Kontynuuje odczyt wielu fragmentów XML, aż do osiągnięcia końca strumienia.</span><span class="sxs-lookup"><span data-stu-id="06d5f-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="06d5f-146">Fragmenty, które <xref:System.Data.DataSet> pasują do schematu są dołączane do odpowiednich tabel.</span><span class="sxs-lookup"><span data-stu-id="06d5f-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="06d5f-147">Fragmenty, które nie <xref:System.Data.DataSet> pasują do schematu są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="06d5f-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="06d5f-148">Jeśli przekażesz **XmlReader** do **ReadXml,** który jest pozycjonowany część drogi do dokumentu XML, **ReadXml** odczyta do następnego węzła elementu i będzie traktować to jako element główny, odczytu do końca węzła elementu tylko.</span><span class="sxs-lookup"><span data-stu-id="06d5f-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="06d5f-149">Nie ma to zastosowania, jeśli określisz **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="06d5f-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="06d5f-150">Jednostki DTD</span><span class="sxs-lookup"><span data-stu-id="06d5f-150">DTD Entities</span></span>  
 <span data-ttu-id="06d5f-151">Jeśli kod XML zawiera jednostki zdefiniowane w schemacie definicji typu dokumentu (DTD), wyjątek zostanie zgłoszony, jeśli spróbujesz załadować <xref:System.Data.DataSet> nazwę pliku, strumień lub niecepwalność **XmlReader** do **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="06d5f-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="06d5f-152">Zamiast tego należy utworzyć **XmlValidatingReader,** z **EntityHandling** ustawiona na **EntityHandling.ExpandEntities**i przekazać **XmlValidatingReader** do **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="06d5f-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="06d5f-153">**XmlValidatingReader** rozwinie jednostki przed odczytaniem <xref:System.Data.DataSet>przez .</span><span class="sxs-lookup"><span data-stu-id="06d5f-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="06d5f-154">Poniższe przykłady kodu pokazują, <xref:System.Data.DataSet> jak załadować ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="06d5f-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="06d5f-155">W pierwszym przykładzie jest wyświetlana nazwa pliku przekazywana do metody **ReadXml.**</span><span class="sxs-lookup"><span data-stu-id="06d5f-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="06d5f-156">Drugi przykład pokazuje ciąg, który zawiera XML jest ładowany przy użyciu pliku <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="06d5f-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="06d5f-157">Jeśli wywołasz **ReadXml,** aby załadować bardzo duży plik, może wystąpić niska wydajność.</span><span class="sxs-lookup"><span data-stu-id="06d5f-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="06d5f-158">Aby zapewnić najlepszą wydajność **dla ReadXml**, <xref:System.Data.DataTable.BeginLoadData%2A> w dużym pliku, wywołaj metodę dla każdej tabeli w programie , a następnie wywołanie <xref:System.Data.DataSet> **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="06d5f-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="06d5f-159">Na koniec <xref:System.Data.DataTable.EndLoadData%2A> wywołaj każdą <xref:System.Data.DataSet>tabelę w , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="06d5f-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="06d5f-160">Jeśli schemat XSD dla <xref:System.Data.DataSet> twojego zawiera **targetNamespace**, dane mogą nie być odczytywane i mogą <xref:System.Data.DataSet> wystąpić wyjątki, podczas wywoływania **ReadXml,** aby załadować z plikiem XML, który zawiera elementy bez kwalifikującego się obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="06d5f-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="06d5f-161">Aby odczytać elementy niekwalifikowane w tym przypadku, ustaw **elementFormDefault** równa "kwalifikowany" w schemacie XSD.</span><span class="sxs-lookup"><span data-stu-id="06d5f-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="06d5f-162">Przykład:</span><span class="sxs-lookup"><span data-stu-id="06d5f-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="06d5f-163">Scalanie danych z XML</span><span class="sxs-lookup"><span data-stu-id="06d5f-163">Merging Data from XML</span></span>  
 <span data-ttu-id="06d5f-164">Jeśli <xref:System.Data.DataSet> już zawiera dane, nowe dane z XML są dodawane <xref:System.Data.DataSet>do danych już obecnych w .</span><span class="sxs-lookup"><span data-stu-id="06d5f-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06d5f-165">**ReadXml** nie scala się z <xref:System.Data.DataSet> pliku XML z żadnymi informacjami o wierszu z pasującymi kluczami podstawowymi.</span><span class="sxs-lookup"><span data-stu-id="06d5f-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="06d5f-166">Aby zastąpić istniejące informacje o wierszu nowymi informacjami z xml, <xref:System.Data.DataSet>użyj <xref:System.Data.DataSet.Merge%2A> **ReadXml,** <xref:System.Data.DataSet>aby utworzyć nowy program , a następnie nowy <xref:System.Data.DataSet> w istniejącym pliku .</span><span class="sxs-lookup"><span data-stu-id="06d5f-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06d5f-167">Należy zauważyć, że ładowanie DiffGram przy użyciu **ReadXML** z **XmlReadMode** **DiffGram** scali wiersze, które mają ten sam unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="06d5f-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d5f-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06d5f-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="06d5f-169">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="06d5f-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="06d5f-170">Elementy DiffGram</span><span class="sxs-lookup"><span data-stu-id="06d5f-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="06d5f-171">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="06d5f-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="06d5f-172">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="06d5f-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="06d5f-173">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="06d5f-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="06d5f-174">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="06d5f-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="06d5f-175">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06d5f-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
