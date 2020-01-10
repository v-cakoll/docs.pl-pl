---
title: Klasa XmlSchemaSet na potrzeby kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709819"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="11169-102">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="11169-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="11169-103">Opisuje <xref:System.Xml.Schema.XmlSchemaSet>, pamięć podręczną, w której można przechowywać i sprawdzać schematy języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="11169-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="11169-104">Klasa XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="11169-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="11169-105"><xref:System.Xml.Schema.XmlSchemaSet> to pamięć podręczna, w której schematy języka definicji schematu XML (XSD) mogą być przechowywane i weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="11169-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="11169-106">W <xref:System.Xml?displayProperty=nameWithType> w wersji 1,0 schematy XML zostały załadowane do klasy <xref:System.Xml.Schema.XmlSchemaCollection> jako biblioteka schematów.</span><span class="sxs-lookup"><span data-stu-id="11169-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="11169-107">W <xref:System.Xml?displayProperty=nameWithType> w wersji 2,0 <xref:System.Xml.XmlValidatingReader> i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są przestarzałe i zostały zastąpione przez metody <xref:System.Xml.XmlReader.Create%2A> oraz odpowiednio do klasy <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="11169-108">Wprowadzono <xref:System.Xml.Schema.XmlSchemaSet>, aby rozwiązać wiele problemów, w tym zgodność ze standardami, wydajność i przestarzały format schematu danych Microsoft XML (XDR).</span><span class="sxs-lookup"><span data-stu-id="11169-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="11169-109">Poniżej znajduje się porównanie klasy <xref:System.Xml.Schema.XmlSchemaCollection> i klasy <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="11169-110">Klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="11169-110">XmlSchemaCollection</span></span>|<span data-ttu-id="11169-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="11169-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="11169-112">Obsługuje schematy XDR i W3C XML firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11169-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="11169-113">Obsługuje tylko schematy W3C XML.</span><span class="sxs-lookup"><span data-stu-id="11169-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="11169-114">Schematy są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="11169-115">Schematy nie są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="11169-116">Zapewnia to poprawę wydajności podczas tworzenia biblioteki schematów.</span><span class="sxs-lookup"><span data-stu-id="11169-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="11169-117">Każdy schemat generuje konkretną kompilację, która może skutkować "wyspami".</span><span class="sxs-lookup"><span data-stu-id="11169-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="11169-118">W związku z tym wszystkie operacje dołączania i importowania są uwzględniane tylko w tym schemacie.</span><span class="sxs-lookup"><span data-stu-id="11169-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="11169-119">Skompilowane schematy generują pojedynczy schemat logiczny "zestaw" schematów.</span><span class="sxs-lookup"><span data-stu-id="11169-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="11169-120">Wszystkie zaimportowane schematy w schemacie, które są dodawane do zestawu, są bezpośrednio dodawane do samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11169-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="11169-121">Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.</span><span class="sxs-lookup"><span data-stu-id="11169-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="11169-122">W kolekcji może istnieć tylko jeden schemat dla konkretnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="11169-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="11169-123">Można dodać wiele schematów dla tej samej docelowej przestrzeni nazw, o ile nie występują konflikty typów.</span><span class="sxs-lookup"><span data-stu-id="11169-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="11169-124">Migrowanie do XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="11169-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="11169-125">Poniższy przykład kodu zawiera Przewodnik migracji do nowej klasy <xref:System.Xml.Schema.XmlSchemaSet> z przestarzałej klasy <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="11169-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="11169-126">Przykład kodu ilustruje następujące główne różnice między tymi dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="11169-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="11169-127">W przeciwieństwie do metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> klasy <xref:System.Xml.Schema.XmlSchemaCollection>, schematy nie są kompilowane podczas wywoływania metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-128">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest jawnie wywoływana w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="11169-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="11169-129">Aby wykonać iterację <xref:System.Xml.Schema.XmlSchemaSet>, należy użyć właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="11169-130">Poniżej znajduje się przestarzały przykład kodu <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="11169-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="11169-131">Poniżej przedstawiono odpowiednik przykładu kodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="11169-132">Dodawanie i pobieranie schematów</span><span class="sxs-lookup"><span data-stu-id="11169-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="11169-133">Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-134">Po dodaniu schematu do <xref:System.Xml.Schema.XmlSchemaSet>jest on skojarzony z docelowym identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="11169-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="11169-135">Docelowy identyfikator URI przestrzeni nazw może być określony jako parametr metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> lub jeśli nie określono docelowej przestrzeni nazw, <xref:System.Xml.Schema.XmlSchemaSet> używa docelowej przestrzeni nazw zdefiniowanej w schemacie.</span><span class="sxs-lookup"><span data-stu-id="11169-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="11169-136">Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-137">Właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> pozwala na iterację <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-138">Właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> zwraca wszystkie obiekty <xref:System.Xml.Schema.XmlSchema> zawarte w <xref:System.Xml.Schema.XmlSchemaSet>lub, uwzględniając docelowy parametr przestrzeni nazw, zwraca wszystkie obiekty <xref:System.Xml.Schema.XmlSchema> należące do docelowej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="11169-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="11169-139">Jeśli `null` jest określony jako docelowy parametr przestrzeni nazw, właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> zwraca wszystkie schematy bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="11169-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="11169-140">Poniższy przykład dodaje schemat `books.xsd` w przestrzeni nazw `http://www.contoso.com/books` do <xref:System.Xml.Schema.XmlSchemaSet>, pobiera wszystkie schematy należące do przestrzeni nazw `http://www.contoso.com/books` z <xref:System.Xml.Schema.XmlSchemaSet>, a następnie zapisuje te schematy na <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="11169-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="11169-141">Aby uzyskać więcej informacji o dodawaniu i pobieraniu schematów z obiektu <xref:System.Xml.Schema.XmlSchemaSet>, zobacz metodę <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> i dokumentację dotyczącą właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="11169-142">Kompilowanie schematów</span><span class="sxs-lookup"><span data-stu-id="11169-142">Compiling Schemas</span></span>  
 <span data-ttu-id="11169-143">Schematy w <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego za pomocą metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11169-144">W przeciwieństwie do przestarzałej klasy <xref:System.Xml.Schema.XmlSchemaCollection>, schematy nie są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="11169-145">Jeśli <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda zostanie wykonana pomyślnie, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="11169-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11169-146">Nie dotyczy właściwości <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A>, jeśli schematy są edytowane podczas <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-147">Aktualizacje poszczególnych schematów w <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="11169-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="11169-148">W związku z tym Właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> może być `true`, mimo że jeden z schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> został zmieniony, o ile żadne schematy nie zostały dodane lub usunięte z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="11169-149">Poniższy przykład dodaje `books.xsd` plik do <xref:System.Xml.Schema.XmlSchemaSet> a następnie wywołuje metodę <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="11169-150">Więcej informacji o kompilowaniu schematów w <xref:System.Xml.Schema.XmlSchemaSet>można znaleźć w dokumentacji dotyczącej metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="11169-151">Przeprzetwarzanie schematów</span><span class="sxs-lookup"><span data-stu-id="11169-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="11169-152">Przeprzetwarzanie schematu w <xref:System.Xml.Schema.XmlSchemaSet> wykonuje wszystkie kroki przetwarzania wstępnego wykonane na schemacie po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="11169-153">Jeśli wywołanie metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powiodło się, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="11169-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="11169-154">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powinna być używana, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po wykonaniu kompilacji przez <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="11169-155">Poniższy przykład ilustruje reprzetwarzanie schematu dodanego do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="11169-156">Po skompilowaniu <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>, a schemat dodany do <xref:System.Xml.Schema.XmlSchemaSet> jest modyfikowany, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> zostanie ustawiona na `true`, mimo że schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="11169-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="11169-157">Wywołanie metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> wykonuje wszystkie przetwarzanie wstępne wykonywane przez metodę <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> i ustawia właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="11169-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="11169-158">Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz dokumentację referencyjną metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="11169-159">Sprawdzanie schematu</span><span class="sxs-lookup"><span data-stu-id="11169-159">Checking for a Schema</span></span>  
 <span data-ttu-id="11169-160">Można użyć metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet>, aby sprawdzić, czy schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-161">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> przyjmuje docelową przestrzeń nazw lub obiekt <xref:System.Xml.Schema.XmlSchema> do sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="11169-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="11169-162">W obu przypadkach Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> zwraca `true`, jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="11169-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="11169-163">Więcej informacji o sprawdzaniu schematu znajduje się w dokumentacji dotyczącej metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="11169-164">Usuwanie schematów</span><span class="sxs-lookup"><span data-stu-id="11169-164">Removing Schemas</span></span>  
 <span data-ttu-id="11169-165">Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-166">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> usuwa określony schemat z <xref:System.Xml.Schema.XmlSchemaSet>, podczas gdy metoda <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> usuwa określony schemat i wszystkie schematy importowane z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="11169-167">Poniższy przykład ilustruje Dodawanie wielu schematów do <xref:System.Xml.Schema.XmlSchemaSet>, a następnie użycie metody <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> w celu usunięcia jednego ze schematów i wszystkich importowanych schematów.</span><span class="sxs-lookup"><span data-stu-id="11169-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="11169-168">Aby uzyskać więcej informacji na temat usuwania schematów z <xref:System.Xml.Schema.XmlSchemaSet>, zapoznaj się z dokumentacją dotyczącą metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.</span><span class="sxs-lookup"><span data-stu-id="11169-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="11169-169">Rozdzielczość schematu i xs: import</span><span class="sxs-lookup"><span data-stu-id="11169-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="11169-170">W poniższych przykładach opisano zachowanie <xref:System.Xml.Schema.XmlSchemaSet> w przypadku importowania schematów, gdy w <xref:System.Xml.Schema.XmlSchemaSet>istnieje wiele schematów dla danego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="11169-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="11169-171">Rozważmy na przykład <xref:System.Xml.Schema.XmlSchemaSet>, który zawiera wiele schematów dla przestrzeni nazw `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="11169-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="11169-172">Schemat o następującej `xs:import` dyrektywie zostanie dodany do <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="11169-173"><xref:System.Xml.Schema.XmlSchemaSet> próbuje zaimportować schemat przestrzeni nazw `http://www.contoso.com` przez załadowanie go z adresu URL `http://www.contoso.com/schema.xsd`.</span><span class="sxs-lookup"><span data-stu-id="11169-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="11169-174">Tylko Deklaracja schematu i typy zadeklarowane w dokumencie schematu są dostępne w schemacie importowania, chociaż istnieją inne dokumenty schematu dla przestrzeni nazw `http://www.contoso.com` w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-175">Jeśli nie można zlokalizować pliku `schema.xsd` pod adresem URL `http://www.contoso.com/schema.xsd`, żaden schemat przestrzeni nazw `http://www.contoso.com` nie zostanie zaimportowany do schematu importowania.</span><span class="sxs-lookup"><span data-stu-id="11169-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="11169-176">Sprawdzanie poprawności dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="11169-176">Validating XML Documents</span></span>  
 <span data-ttu-id="11169-177">Dokumenty XML można sprawdzić pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="11169-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="11169-178">Sprawdzanie poprawności dokumentu XML przez dodanie schematu do właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>obiektu <xref:System.Xml.XmlReaderSettings> lub przez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="11169-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="11169-179">Obiekt <xref:System.Xml.XmlReaderSettings> jest następnie używany przez metodę <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader> do tworzenia obiektu <xref:System.Xml.XmlReader> i sprawdzania poprawności dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="11169-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="11169-180">Aby uzyskać więcej informacji na temat walidacji dokumentów XML przy użyciu <xref:System.Xml.Schema.XmlSchemaSet>, zobacz [Walidacja schematu XML (XSD) z](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)zestawem XmlSchemaSet.</span><span class="sxs-lookup"><span data-stu-id="11169-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11169-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11169-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="11169-182">XmlSchemaSet jako pamięć podręczna schematów</span><span class="sxs-lookup"><span data-stu-id="11169-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="11169-183">Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="11169-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
