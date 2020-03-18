---
title: Omówienie klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167897"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="fa4ea-102">Omówienie klasy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="fa4ea-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="fa4ea-103">Klasa <xref:System.Xml.Linq.XElement> jest jedną z podstawowych [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]klas w .</span><span class="sxs-lookup"><span data-stu-id="fa4ea-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="fa4ea-104">Reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-104">It represents an XML element.</span></span> <span data-ttu-id="fa4ea-105">Ta klasa służy do tworzenia elementów; zmienić zawartość elementu; dodawanie, zmienianie lub usuwanie elementów podrzędnych; dodawanie atrybutów do elementu; lub serializować zawartość elementu w formie tekstowej.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="fa4ea-106">Można również współpracować z <xref:System.Xml?displayProperty=nameWithType>innymi klasami <xref:System.Xml.XmlWriter>w <xref:System.Xml.Xsl.XslCompiledTransform>, takich jak <xref:System.Xml.XmlReader>, , i .</span><span class="sxs-lookup"><span data-stu-id="fa4ea-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="fa4ea-107">W tym temacie opisano <xref:System.Xml.Linq.XElement> funkcje dostarczane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="fa4ea-108">Konstruowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="fa4ea-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="fa4ea-109">Drzewa XML można konstruować na różne sposoby, w tym na następujące sposoby:</span><span class="sxs-lookup"><span data-stu-id="fa4ea-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="fa4ea-110">Można skonstruować drzewo XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="fa4ea-111">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="fa4ea-112">Można analizować XML z różnych źródeł, <xref:System.IO.TextReader>w tym z plików tekstowych lub adresu URL.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="fa4ea-113">Aby uzyskać więcej informacji, zobacz [Analizowanie języka XML (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="fa4ea-114">Można użyć <xref:System.Xml.XmlReader> do wypełnienia drzewa.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="fa4ea-115">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="fa4ea-116">Jeśli masz moduł, który można <xref:System.Xml.XmlWriter>zapisywać zawartość <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do , można użyć metody do utworzenia modułu zapisującego, przekazać <xref:System.Xml.XmlWriter> moduł umodułu, a następnie użyć zawartości, która jest zapisywana do wypełnienia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="fa4ea-117">Jednak najczęstszym sposobem tworzenia drzewa XML jest następujący:</span><span class="sxs-lookup"><span data-stu-id="fa4ea-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="fa4ea-118">Inną bardzo często techniką tworzenia drzewa XML polega na wykorzystaniu wyników kwerendy LINQ do wypełnienia drzewa XML, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fa4ea-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="fa4ea-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa4ea-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="fa4ea-120">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="fa4ea-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="fa4ea-121">Drzewo XML można serializować na <xref:System.IO.File>, <xref:System.IO.TextWriter>a <xref:System.Xml.XmlWriter>, lub .</span><span class="sxs-lookup"><span data-stu-id="fa4ea-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="fa4ea-122">Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XML (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="fa4ea-123">Pobieranie danych XML za pomocą metod osi</span><span class="sxs-lookup"><span data-stu-id="fa4ea-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="fa4ea-124">Metody osi można używać do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów elementów przodka.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="fa4ea-125">Zapytania LINQ działają na metodach osi i zapewniają kilka elastycznych i zaawansowanych sposobów poruszania się po drzewie XML i przetwarzania go.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="fa4ea-126">Aby uzyskać więcej informacji, zobacz [LINQ do XML Axes (C#)](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="fa4ea-127">Tworzenie zapytań dotyczących drzew XML</span><span class="sxs-lookup"><span data-stu-id="fa4ea-127">Querying XML Trees</span></span>  
 <span data-ttu-id="fa4ea-128">Można napisać zapytania LINQ, które wyodrębniają dane z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="fa4ea-129">Aby uzyskać więcej informacji, zobacz [Wykonywanie kwerenddrzew XML (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="fa4ea-130">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="fa4ea-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="fa4ea-131">Element można modyfikować na różne sposoby, w tym zmieniać jego zawartość lub atrybuty.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="fa4ea-132">Można również usunąć element z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fa4ea-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="fa4ea-133">Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fa4ea-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ea-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa4ea-134">See also</span></span>

- [<span data-ttu-id="fa4ea-135">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fa4ea-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
