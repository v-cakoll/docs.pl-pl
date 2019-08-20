---
title: XElement — Omówienie klasyC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: e742741f56f3e39f93b9f1d6be30a54a4ede67f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590879"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="96c9f-102">XElement — Omówienie klasyC#()</span><span class="sxs-lookup"><span data-stu-id="96c9f-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="96c9f-103">Klasa jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="96c9f-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="96c9f-104">Reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="96c9f-104">It represents an XML element.</span></span> <span data-ttu-id="96c9f-105">Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej.</span><span class="sxs-lookup"><span data-stu-id="96c9f-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="96c9f-106">Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="96c9f-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="96c9f-107">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="96c9f-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="96c9f-108">Konstruowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="96c9f-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="96c9f-109">Drzewa XML można konstruować na różne sposoby, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="96c9f-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="96c9f-110">Drzewo XML można skonstruować w kodzie.</span><span class="sxs-lookup"><span data-stu-id="96c9f-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="96c9f-111">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XMLC#()](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="96c9f-112">Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>plików tekstowych lub adresów sieci Web (URL).</span><span class="sxs-lookup"><span data-stu-id="96c9f-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="96c9f-113">Aby uzyskać więcej informacji, zobacz [Analizowanie XMLC#()](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="96c9f-114">Aby wypełnić drzewo, <xref:System.Xml.XmlReader> można użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="96c9f-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="96c9f-115">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="96c9f-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="96c9f-116">Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XContainer.CreateWriter%2A> programie, możesz użyć metody do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej <xref:System.Xml.XmlWriter> w programie w celu wypełnienia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="96c9f-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="96c9f-117">Jednak najbardziej typowym sposobem tworzenia drzewa XML jest:</span><span class="sxs-lookup"><span data-stu-id="96c9f-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="96c9f-118">Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do wypełnienia drzewa XML, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="96c9f-118">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="96c9f-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96c9f-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="96c9f-120">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="96c9f-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="96c9f-121">Można serializować drzewo XML do <xref:System.IO.File>, a <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="96c9f-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="96c9f-122">Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XMLC#()](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="96c9f-123">Pobieranie danych XML za pomocą metod osi</span><span class="sxs-lookup"><span data-stu-id="96c9f-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="96c9f-124">Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="96c9f-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="96c9f-125">zapytania działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania w drzewie XML i przetwarzania ich.</span><span class="sxs-lookup"><span data-stu-id="96c9f-125">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="96c9f-126">Aby uzyskać więcej informacji, zobacz [LINQ to XML osiC#()](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="96c9f-127">Tworzenie zapytań dotyczących drzew XML</span><span class="sxs-lookup"><span data-stu-id="96c9f-127">Querying XML Trees</span></span>  
 <span data-ttu-id="96c9f-128">Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyodrębniające dane z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="96c9f-128">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="96c9f-129">Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczącychC#drzew XML ()](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="96c9f-130">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="96c9f-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="96c9f-131">Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty.</span><span class="sxs-lookup"><span data-stu-id="96c9f-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="96c9f-132">Można również usunąć element z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="96c9f-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="96c9f-133">Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="96c9f-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c9f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96c9f-134">See also</span></span>

- [<span data-ttu-id="96c9f-135">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="96c9f-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
