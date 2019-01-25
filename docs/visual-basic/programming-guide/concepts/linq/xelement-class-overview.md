---
title: Przegląd klasy XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: fe2a91d2b286061453e41870d68c04424417c6ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628819"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="1f2bd-102">Przegląd klasy XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f2bd-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="1f2bd-103"><xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f2bd-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="1f2bd-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-104">It represents an XML element.</span></span> <span data-ttu-id="1f2bd-105">Ta klasa służy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodawanie atrybutów do elementu; lub serializacji zawartość elementu w postaci tekstu.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="1f2bd-106">Może również współpracować z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="1f2bd-107">Funkcje klasy XElement</span><span class="sxs-lookup"><span data-stu-id="1f2bd-107">XElement Functionality</span></span>  
 <span data-ttu-id="1f2bd-108">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="1f2bd-109">Konstruowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="1f2bd-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="1f2bd-110">Możesz utworzyć drzew XML na różne sposoby, m.in. następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1f2bd-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="1f2bd-111">Można skonstruować drzewa XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="1f2bd-112">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="1f2bd-113">Można teraz analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adres internetowy (URL).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="1f2bd-114">Aby uzyskać więcej informacji, zobacz [analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="1f2bd-115">Możesz użyć <xref:System.Xml.XmlReader> do wypełniania drzewa.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="1f2bd-116">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="1f2bd-117">Jeśli masz moduł, który może zapisać zawartości <xref:System.Xml.XmlWriter>, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, przekazać moduł zapisujący do modułu, a następnie użyć zawartości, który jest zapisywany <xref:System.Xml.XmlWriter> do wypełnianie drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="1f2bd-118">Jednak Najczęstszym sposobem tworzenia drzewa XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1f2bd-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="1f2bd-119">Inna technika bardzo często do tworzenia drzewa XML polega na wykorzystaniu wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnianie drzewa XML, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1f2bd-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="1f2bd-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1f2bd-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="1f2bd-121">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="1f2bd-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="1f2bd-122">Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="1f2bd-123">Aby uzyskać więcej informacji, zobacz [serializowanie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="1f2bd-124">Pobieranie danych XML przy użyciu metody osi</span><span class="sxs-lookup"><span data-stu-id="1f2bd-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="1f2bd-125">Można użyć metody osi, można pobrać atrybutów, elementy podrzędne, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="1f2bd-126">zapytania działają na metody osi i zapewniają kilka metod elastycznym i zaawansowanym nawigowania i przetworzyć drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-126">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="1f2bd-127">Aby uzyskać więcej informacji, zobacz [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="1f2bd-128">Tworzenie zapytań drzew XML</span><span class="sxs-lookup"><span data-stu-id="1f2bd-128">Querying XML Trees</span></span>  
 <span data-ttu-id="1f2bd-129">Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które umożliwiają wyodrębnianie danych z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="1f2bd-130">Aby uzyskać więcej informacji, zobacz [zapytań drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="1f2bd-131">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="1f2bd-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="1f2bd-132">Można zmodyfikować elementu na różne sposoby, m.in. zmiana jego zawartości lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="1f2bd-133">Można również usunąć element, po swoim obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="1f2bd-134">Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2bd-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f2bd-135">See also</span></span>
- [<span data-ttu-id="1f2bd-136">LINQ to XML — przegląd programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f2bd-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
