---
title: Przegląd klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 49b3b81276a598d003efa98337dd945576d802ca
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925106"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="2fcd0-102">Przegląd klasy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="2fcd0-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="2fcd0-103"><xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2fcd0-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="2fcd0-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-104">It represents an XML element.</span></span> <span data-ttu-id="2fcd0-105">Ta klasa służy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodawanie atrybutów do elementu; lub serializacji zawartość elementu w postaci tekstu.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="2fcd0-106">Może również współpracować z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="2fcd0-107">Funkcje klasy XElement</span><span class="sxs-lookup"><span data-stu-id="2fcd0-107">XElement Functionality</span></span>  
 <span data-ttu-id="2fcd0-108">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="2fcd0-109">Konstruowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="2fcd0-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="2fcd0-110">Możesz utworzyć drzew XML na różne sposoby, m.in. następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2fcd0-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="2fcd0-111">Można skonstruować drzewa XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="2fcd0-112">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="2fcd0-113">Można teraz analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adres internetowy (URL).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="2fcd0-114">Aby uzyskać więcej informacji, zobacz [analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="2fcd0-115">Możesz użyć <xref:System.Xml.XmlReader> do wypełniania drzewa.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="2fcd0-116">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="2fcd0-117">Jeśli masz moduł, który może zapisać zawartości <xref:System.Xml.XmlWriter>, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, przekazać moduł zapisujący do modułu, a następnie użyć zawartości, który jest zapisywany <xref:System.Xml.XmlWriter> do wypełnianie drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="2fcd0-118">Jednak Najczęstszym sposobem tworzenia drzewa XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="2fcd0-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="2fcd0-119">Inna technika bardzo często do tworzenia drzewa XML polega na wykorzystaniu wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnianie drzewa XML, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2fcd0-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="2fcd0-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2fcd0-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="2fcd0-121">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="2fcd0-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="2fcd0-122">Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="2fcd0-123">Aby uzyskać więcej informacji, zobacz [serializowanie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="2fcd0-124">Pobieranie danych XML przy użyciu metody osi</span><span class="sxs-lookup"><span data-stu-id="2fcd0-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="2fcd0-125">Można użyć metody osi, można pobrać atrybutów, elementy podrzędne, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="2fcd0-126"> zapytania działają na metody osi i zapewniają kilka metod elastycznym i zaawansowanym nawigowania i przetworzyć drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="2fcd0-127">Aby uzyskać więcej informacji, zobacz [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="2fcd0-128">Tworzenie zapytań drzew XML</span><span class="sxs-lookup"><span data-stu-id="2fcd0-128">Querying XML Trees</span></span>  
 <span data-ttu-id="2fcd0-129">Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które umożliwiają wyodrębnianie danych z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="2fcd0-130">Aby uzyskać więcej informacji, zobacz [zapytań drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="2fcd0-131">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="2fcd0-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="2fcd0-132">Można zmodyfikować elementu na różne sposoby, m.in. zmiana jego zawartości lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="2fcd0-133">Można również usunąć element, po swoim obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="2fcd0-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="2fcd0-134">Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd0-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fcd0-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fcd0-135">See Also</span></span>  
 [<span data-ttu-id="2fcd0-136">LINQ to XML — przegląd programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="2fcd0-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
