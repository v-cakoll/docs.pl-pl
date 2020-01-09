---
title: XElement — Omówienie klasyC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: d77c725b3c786b8a8fa2b0eeab4bc4b30f298218
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635473"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="3eb45-102">XElement — Omówienie klasyC#()</span><span class="sxs-lookup"><span data-stu-id="3eb45-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="3eb45-103">Klasa <xref:System.Xml.Linq.XElement> jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3eb45-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="3eb45-104">Reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="3eb45-104">It represents an XML element.</span></span> <span data-ttu-id="3eb45-105">Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej.</span><span class="sxs-lookup"><span data-stu-id="3eb45-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="3eb45-106">Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3eb45-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="3eb45-107">W tym temacie opisano funkcje udostępniane przez klasę <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3eb45-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="3eb45-108">Konstruowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="3eb45-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="3eb45-109">Drzewa XML można konstruować na różne sposoby, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="3eb45-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="3eb45-110">Drzewo XML można skonstruować w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3eb45-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="3eb45-111">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XMLC#()](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="3eb45-112">Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adresy sieci Web (URL).</span><span class="sxs-lookup"><span data-stu-id="3eb45-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="3eb45-113">Aby uzyskać więcej informacji, zobacz [Analizowanie XMLC#()](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="3eb45-114">Aby wypełnić drzewo, można użyć <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3eb45-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="3eb45-115">Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="3eb45-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="3eb45-116">Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter>, możesz użyć metody <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej w <xref:System.Xml.XmlWriter>, aby wypełnić drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="3eb45-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="3eb45-117">Jednak najbardziej typowym sposobem tworzenia drzewa XML jest:</span><span class="sxs-lookup"><span data-stu-id="3eb45-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="3eb45-118">Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników zapytania LINQ do wypełnienia drzewa XML, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3eb45-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="3eb45-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3eb45-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="3eb45-120">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="3eb45-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="3eb45-121">Można serializować drzewo XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3eb45-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="3eb45-122">Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XMLC#()](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="3eb45-123">Pobieranie danych XML za pomocą metod osi</span><span class="sxs-lookup"><span data-stu-id="3eb45-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="3eb45-124">Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3eb45-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="3eb45-125">Zapytania LINQ działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania i przetwarzania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3eb45-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="3eb45-126">Aby uzyskać więcej informacji, zobacz [LINQ to XML osiC#()](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="3eb45-127">Tworzenie zapytań dotyczących drzew XML</span><span class="sxs-lookup"><span data-stu-id="3eb45-127">Querying XML Trees</span></span>  
 <span data-ttu-id="3eb45-128">Można napisać zapytania LINQ wyodrębniające dane z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3eb45-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="3eb45-129">Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczącychC#drzew XML ()](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="3eb45-130">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="3eb45-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="3eb45-131">Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty.</span><span class="sxs-lookup"><span data-stu-id="3eb45-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="3eb45-132">Można również usunąć element z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3eb45-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="3eb45-133">Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3eb45-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb45-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3eb45-134">See also</span></span>

- [<span data-ttu-id="3eb45-135">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3eb45-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
