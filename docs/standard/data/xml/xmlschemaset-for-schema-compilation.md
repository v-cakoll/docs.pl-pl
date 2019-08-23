---
title: Klasa XmlSchemaSet na potrzeby kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e05b09d5ce788b9a3da262d5890a0694b49375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969030"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="029b7-102">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="029b7-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="029b7-103">Opisuje pamięć podręczną, w której można przechowywać i sprawdzać schematy języka definicji schematu XML (XSD). <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="029b7-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="029b7-104">Klasa XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="029b7-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="029b7-105">Jest <xref:System.Xml.Schema.XmlSchemaSet> pamięcią podręczną, w której schematy języka definicji schematu XML (XSD) mogą być przechowywane i weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="029b7-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="029b7-106">W <xref:System.Xml?displayProperty=nameWithType> wersji 1,0 schematy XML zostały załadowane <xref:System.Xml.Schema.XmlSchemaCollection> do klasy jako biblioteka schematów.</span><span class="sxs-lookup"><span data-stu-id="029b7-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="029b7-107">W <xref:System.Xml?displayProperty=nameWithType> wersji 2,0 <xref:System.Xml.XmlValidatingReader> , i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są <xref:System.Xml.XmlReader.Create%2A> przestarzałe i zostały zastąpione metodami oraz <xref:System.Xml.Schema.XmlSchemaSet> klasą.</span><span class="sxs-lookup"><span data-stu-id="029b7-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="029b7-108"><xref:System.Xml.Schema.XmlSchemaSet> Wprowadzono rozwiązanie do rozwiązywania problemów, takich jak zgodność ze standardami, wydajność i przestarzały format schematu Microsoft XML — zmniejszone (XDR).</span><span class="sxs-lookup"><span data-stu-id="029b7-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="029b7-109">Poniżej znajduje się porównanie <xref:System.Xml.Schema.XmlSchemaCollection> klasy <xref:System.Xml.Schema.XmlSchemaSet> i klasy.</span><span class="sxs-lookup"><span data-stu-id="029b7-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="029b7-110">Klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="029b7-110">XmlSchemaCollection</span></span>|<span data-ttu-id="029b7-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="029b7-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="029b7-112">Obsługuje schematy XDR i W3C XML firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="029b7-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="029b7-113">Obsługuje tylko schematy W3C XML.</span><span class="sxs-lookup"><span data-stu-id="029b7-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="029b7-114">Schematy są kompilowane, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> gdy wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="029b7-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="029b7-115">Schematy nie są kompilowane, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> gdy wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="029b7-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="029b7-116">Zapewnia to poprawę wydajności podczas tworzenia biblioteki schematów.</span><span class="sxs-lookup"><span data-stu-id="029b7-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="029b7-117">Każdy schemat generuje konkretną kompilację, która może skutkować "wyspami".</span><span class="sxs-lookup"><span data-stu-id="029b7-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="029b7-118">W związku z tym wszystkie operacje dołączania i importowania są uwzględniane tylko w tym schemacie.</span><span class="sxs-lookup"><span data-stu-id="029b7-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="029b7-119">Skompilowane schematy generują pojedynczy schemat logiczny "zestaw" schematów.</span><span class="sxs-lookup"><span data-stu-id="029b7-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="029b7-120">Wszystkie zaimportowane schematy w schemacie, które są dodawane do zestawu, są bezpośrednio dodawane do samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="029b7-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="029b7-121">Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.</span><span class="sxs-lookup"><span data-stu-id="029b7-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="029b7-122">W kolekcji może istnieć tylko jeden schemat dla konkretnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="029b7-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="029b7-123">Można dodać wiele schematów dla tej samej docelowej przestrzeni nazw, o ile nie występują konflikty typów.</span><span class="sxs-lookup"><span data-stu-id="029b7-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="029b7-124">Migrowanie do XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="029b7-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="029b7-125">Poniższy przykład kodu zawiera Przewodnik migracji do nowej <xref:System.Xml.Schema.XmlSchemaSet> klasy z klasy przestarzałej. <xref:System.Xml.Schema.XmlSchemaCollection></span><span class="sxs-lookup"><span data-stu-id="029b7-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="029b7-126">Przykład kodu ilustruje następujące główne różnice między tymi dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="029b7-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="029b7-127">W przeciwieństwie <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> do metody <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> nie są kompilowane podczas <xref:System.Xml.Schema.XmlSchemaSet>wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="029b7-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda<xref:System.Xml.Schema.XmlSchemaSet> jest jawnie wywoływana w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="029b7-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="029b7-129">Aby wykonać iterację <xref:System.Xml.Schema.XmlSchemaSet>w <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> programie, należy użyć właściwości <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="029b7-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="029b7-130">Poniżej znajduje się przestarzały <xref:System.Xml.Schema.XmlSchemaCollection> przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="029b7-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="029b7-131">Poniżej znajduje się odpowiedni <xref:System.Xml.Schema.XmlSchemaSet> przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="029b7-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="029b7-132">Dodawanie i pobieranie schematów</span><span class="sxs-lookup"><span data-stu-id="029b7-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="029b7-133">Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="029b7-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-134">Gdy schemat zostanie dodany do elementu <xref:System.Xml.Schema.XmlSchemaSet>, jest on skojarzony z docelowym identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="029b7-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="029b7-135">Docelowy identyfikator URI przestrzeni nazw może być określony jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody lub jeśli nie określono docelowej przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet> , używa docelowej przestrzeni nazw zdefiniowanej w schemacie.</span><span class="sxs-lookup"><span data-stu-id="029b7-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="029b7-136">Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> użycia właściwości <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="029b7-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-137">Właściwość elementu umożliwia wykonywanie iteracji względem <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="029b7-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-138">Właściwość zwraca <xref:System.Xml.Schema.XmlSchemaSet>wszystkie obiekty zawarte w, lub, pod <xref:System.Xml.Schema.XmlSchema> którym znajduje się docelowy parametr przestrzeni nazw, zwraca wszystkie obiekty należące do docelowej przestrzeni nazw. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A></span><span class="sxs-lookup"><span data-stu-id="029b7-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="029b7-139">Jeśli `null` jest określony jako docelowy parametr przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> , właściwość zwraca wszystkie schematy bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="029b7-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="029b7-140">`books.xsd` Poniższy przykład dodaje schemat `http://www.contoso.com/books` w przestrzeni nazw do <xref:System.Xml.Schema.XmlSchemaSet>elementu `http://www.contoso.com/books` , pobiera wszystkie <xref:System.Xml.Schema.XmlSchemaSet>schematy należące do <xref:System.Console>przestrzeni nazw z, a następnie zapisuje te schematy do.</span><span class="sxs-lookup"><span data-stu-id="029b7-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="029b7-141">Aby uzyskać więcej informacji o dodawaniu i pobieraniu <xref:System.Xml.Schema.XmlSchemaSet> schematów z obiektu, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> zapoznaj się <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> z dokumentacją dotyczącą metody i odwołania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="029b7-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="029b7-142">Kompilowanie schematów</span><span class="sxs-lookup"><span data-stu-id="029b7-142">Compiling Schemas</span></span>  
 <span data-ttu-id="029b7-143">Schematy w elemencie <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> za pomocą metody <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="029b7-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="029b7-144">W przeciwieństwie do <xref:System.Xml.Schema.XmlSchemaCollection> przestarzałej klasy, schematy nie są kompilowane <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> , gdy wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="029b7-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="029b7-145">Jeśli metoda zostanie wykonana pomyślnie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , właściwość `true`jest ustawiona na. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A></span><span class="sxs-lookup"><span data-stu-id="029b7-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="029b7-146">Nie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> ma to żadnego oddziaływania, jeśli schematy są edytowane <xref:System.Xml.Schema.XmlSchemaSet>w trakcie.</span><span class="sxs-lookup"><span data-stu-id="029b7-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-147">Aktualizacje poszczególnych schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="029b7-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="029b7-148"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> W związku z tym właściwość może być `true` nawet pomimo tego, że jeden z schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> został zmieniony, o ile <xref:System.Xml.Schema.XmlSchemaSet>żadne schematy nie zostały dodane lub usunięte z.</span><span class="sxs-lookup"><span data-stu-id="029b7-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="029b7-149">Poniższy przykład dodaje `books.xsd` plik <xref:System.Xml.Schema.XmlSchemaSet> do a następnie wywołuje <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="029b7-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="029b7-150">Więcej informacji o kompilowaniu schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> znajduje się w dokumentacji dotyczącej metod.</span><span class="sxs-lookup"><span data-stu-id="029b7-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="029b7-151">Przeprzetwarzanie schematów</span><span class="sxs-lookup"><span data-stu-id="029b7-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="029b7-152">Przeprzetwarzanie schematu w programie <xref:System.Xml.Schema.XmlSchemaSet> wykonuje wszystkie kroki przetwarzania wstępnego wykonane na schemacie, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> gdy wywoływana <xref:System.Xml.Schema.XmlSchemaSet> jest metoda obiektu.</span><span class="sxs-lookup"><span data-stu-id="029b7-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="029b7-153">Jeśli wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody zakończyło się pomyślnie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , właściwość <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="029b7-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="029b7-154">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powinna być używana, gdy schemat <xref:System.Xml.Schema.XmlSchemaSet> w programie <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po wykonaniu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="029b7-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="029b7-155">Poniższy przykład ilustruje przetworzenie schematu dodanego do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="029b7-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="029b7-156"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> `true` <xref:System.Xml.Schema.XmlSchemaSet> Po skompilowaniu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> przy użyciu metody, a schemat dodany do elementu jest modyfikowany, właściwość jest ustawiona na, nawet jeśli schemat w został zmodyfikowany. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="029b7-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="029b7-157">Wywołanie metody wykonuje wszystkie przetwarzanie wstępne wykonywane <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> przez <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> metodę i ustawia właściwość na `false`. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A></span><span class="sxs-lookup"><span data-stu-id="029b7-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="029b7-158">Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w programie <xref:System.Xml.Schema.XmlSchemaSet>, <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Zobacz dokumentację referencyjną metody.</span><span class="sxs-lookup"><span data-stu-id="029b7-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="029b7-159">Sprawdzanie schematu</span><span class="sxs-lookup"><span data-stu-id="029b7-159">Checking for a Schema</span></span>  
 <span data-ttu-id="029b7-160">Można użyć <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metody, <xref:System.Xml.Schema.XmlSchemaSet> aby sprawdzić, czy <xref:System.Xml.Schema.XmlSchemaSet>schemat jest zawarty w.</span><span class="sxs-lookup"><span data-stu-id="029b7-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-161">Metoda przyjmuje docelowy obszar nazw <xref:System.Xml.Schema.XmlSchema> lub obiekt, który ma zostać wyszukany. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A></span><span class="sxs-lookup"><span data-stu-id="029b7-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="029b7-162">W obu przypadkach <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda zwraca `true` , jeśli <xref:System.Xml.Schema.XmlSchemaSet>schemat jest zawarty w; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="029b7-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="029b7-163">Aby uzyskać więcej informacji na temat sprawdzania schematu, zapoznaj <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> się z dokumentacją dotyczącą metod.</span><span class="sxs-lookup"><span data-stu-id="029b7-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="029b7-164">Usuwanie schematów</span><span class="sxs-lookup"><span data-stu-id="029b7-164">Removing Schemas</span></span>  
 <span data-ttu-id="029b7-165"><xref:System.Xml.Schema.XmlSchemaSet> Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> używania metod <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>i.</span><span class="sxs-lookup"><span data-stu-id="029b7-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-166">Metoda usuwa określony schemat <xref:System.Xml.Schema.XmlSchemaSet>z, podczas gdy <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Metoda usuwa określony schemat i wszystkie schematy importowane z programu <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="029b7-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="029b7-167">Poniższy przykład ilustruje Dodawanie wielu schematów do obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> za pomocą metody usuwania jednego ze schematów i wszystkich importowanych schematów.</span><span class="sxs-lookup"><span data-stu-id="029b7-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="029b7-168">Aby uzyskać więcej informacji na temat usuwania schematów <xref:System.Xml.Schema.XmlSchemaSet>z programu, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> zobacz <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> dokumentację dotyczącą metod i.</span><span class="sxs-lookup"><span data-stu-id="029b7-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="029b7-169">Rozdzielczość schematu i xs: import</span><span class="sxs-lookup"><span data-stu-id="029b7-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="029b7-170">W poniższych przykładach opisano <xref:System.Xml.Schema.XmlSchemaSet> zachowanie importowania schematów, <xref:System.Xml.Schema.XmlSchemaSet>gdy istnieje wiele schematów dla danego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="029b7-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="029b7-171">Rozważmy <xref:System.Xml.Schema.XmlSchemaSet> na przykład, że zawiera wiele schematów `http://www.contoso.com` dla przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="029b7-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="029b7-172">Schemat z poniższą `xs:import` dyrektywą zostanie dodany <xref:System.Xml.Schema.XmlSchemaSet>do.</span><span class="sxs-lookup"><span data-stu-id="029b7-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="029b7-173">Próbuje zaimportować schemat `http://www.contoso.com` dla przestrzeni nazw `http://www.contoso.com/schema.xsd` przez załadowanie go z adresu URL. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="029b7-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="029b7-174">Tylko Deklaracja schematu i typy zadeklarowane w dokumencie schematu są dostępne w schemacie importowania, chociaż istnieją inne dokumenty schematu dla `http://www.contoso.com` przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet>w.</span><span class="sxs-lookup"><span data-stu-id="029b7-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-175">Jeśli plik nie może znajdować się `http://www.contoso.com/schema.xsd` pod adresem URL `http://www.contoso.com` , żaden schemat przestrzeni nazw nie zostanie zaimportowany do schematu importowania. `schema.xsd`</span><span class="sxs-lookup"><span data-stu-id="029b7-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="029b7-176">Sprawdzanie poprawności dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="029b7-176">Validating XML Documents</span></span>  
 <span data-ttu-id="029b7-177">Dokumenty XML można sprawdzić pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="029b7-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="029b7-178">Sprawdzanie poprawności dokumentu XML przez dodanie <xref:System.Xml.Schema.XmlSchemaSet> schematu do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu lub <xref:System.Xml.XmlReaderSettings> poprzez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="029b7-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="029b7-179">Obiekt jest następnie używany <xref:System.Xml.XmlReader.Create%2A> przez metodę <xref:System.Xml.XmlReader> klasy w celu utworzenia <xref:System.Xml.XmlReader> obiektu i zweryfikowania dokumentu XML. <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="029b7-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="029b7-180">Aby uzyskać więcej informacji na temat walidacji dokumentów <xref:System.Xml.Schema.XmlSchemaSet>XML przy użyciu, zobacz [Walidacja schematu XML (XSD) z](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)zestawem XmlSchemaSet.</span><span class="sxs-lookup"><span data-stu-id="029b7-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029b7-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="029b7-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="029b7-182">XmlSchemaSet jako pamięć podręczna schematów</span><span class="sxs-lookup"><span data-stu-id="029b7-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="029b7-183">Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="029b7-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
