---
title: Przegląd klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 815b7b6523afe7106fcdcbe242d667c5ad6aa56e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487018"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="1b428-102">Przegląd klasy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="1b428-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="1b428-103"><xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b428-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="1b428-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="1b428-104">It represents an XML element.</span></span> <span data-ttu-id="1b428-105">Ta klasa służy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodawanie atrybutów do elementu; lub serializacji zawartość elementu w postaci tekstu.</span><span class="sxs-lookup"><span data-stu-id="1b428-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="1b428-106">Może również współpracować z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1b428-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="1b428-107">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="1b428-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="1b428-108">Konstruowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="1b428-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="1b428-109">Możesz utworzyć drzew XML na różne sposoby, m.in. następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1b428-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="1b428-110">Można skonstruować drzewa XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b428-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="1b428-111">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-111">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="1b428-112">Można teraz analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adres internetowy (URL).</span><span class="sxs-lookup"><span data-stu-id="1b428-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="1b428-113">Aby uzyskać więcej informacji, zobacz [analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-113">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="1b428-114">Możesz użyć <xref:System.Xml.XmlReader> do wypełniania drzewa.</span><span class="sxs-lookup"><span data-stu-id="1b428-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="1b428-115">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b428-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="1b428-116">Jeśli masz moduł, który może zapisać zawartości <xref:System.Xml.XmlWriter>, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, przekazać moduł zapisujący do modułu, a następnie użyć zawartości, który jest zapisywany <xref:System.Xml.XmlWriter> do wypełnianie drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1b428-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="1b428-117">Jednak Najczęstszym sposobem tworzenia drzewa XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1b428-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="1b428-118">Inna technika bardzo często do tworzenia drzewa XML polega na wykorzystaniu wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnianie drzewa XML, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b428-118">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="1b428-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1b428-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="1b428-120">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="1b428-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="1b428-121">Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1b428-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="1b428-122">Aby uzyskać więcej informacji, zobacz [serializowanie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-122">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="1b428-123">Pobieranie danych XML przy użyciu metody osi</span><span class="sxs-lookup"><span data-stu-id="1b428-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="1b428-124">Można użyć metody osi, można pobrać atrybutów, elementy podrzędne, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1b428-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="1b428-125">zapytania działają na metody osi i zapewniają kilka metod elastycznym i zaawansowanym nawigowania i przetworzyć drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1b428-125">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="1b428-126">Aby uzyskać więcej informacji, zobacz [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-126">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="1b428-127">Tworzenie zapytań dotyczących drzew XML</span><span class="sxs-lookup"><span data-stu-id="1b428-127">Querying XML Trees</span></span>  
 <span data-ttu-id="1b428-128">Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które umożliwiają wyodrębnianie danych z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1b428-128">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="1b428-129">Aby uzyskać więcej informacji, zobacz [zapytań drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-129">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="1b428-130">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="1b428-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="1b428-131">Można zmodyfikować elementu na różne sposoby, m.in. zmiana jego zawartości lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1b428-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="1b428-132">Można również usunąć element, po swoim obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1b428-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="1b428-133">Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1b428-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b428-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b428-134">See also</span></span>

- [<span data-ttu-id="1b428-135">LINQ to XML — przegląd programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="1b428-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
