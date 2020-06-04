---
title: XElement, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413222"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="850a2-102">Przegląd klasy XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a2-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="850a2-103"><xref:System.Xml.Linq.XElement>Klasa jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="850a2-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="850a2-104">Reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="850a2-104">It represents an XML element.</span></span> <span data-ttu-id="850a2-105">Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej.</span><span class="sxs-lookup"><span data-stu-id="850a2-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="850a2-106">Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType> , takich jak <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> , i <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="850a2-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="850a2-107">Funkcja XElement</span><span class="sxs-lookup"><span data-stu-id="850a2-107">XElement Functionality</span></span>  
 <span data-ttu-id="850a2-108">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="850a2-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="850a2-109">Konstruowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="850a2-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="850a2-110">Drzewa XML można konstruować na różne sposoby, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="850a2-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="850a2-111">Drzewo XML można skonstruować w kodzie.</span><span class="sxs-lookup"><span data-stu-id="850a2-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="850a2-112">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="850a2-113">Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader> plików tekstowych lub adresów sieci Web (URL).</span><span class="sxs-lookup"><span data-stu-id="850a2-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="850a2-114">Aby uzyskać więcej informacji, zobacz [Analizowanie XML (Visual Basic)](parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-114">For more information, see [Parsing XML (Visual Basic)](parsing-xml.md).</span></span>  
  
- <span data-ttu-id="850a2-115"><xref:System.Xml.XmlReader>Aby wypełnić drzewo, można użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="850a2-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="850a2-116">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="850a2-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="850a2-117">Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter> programie, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metody do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej w programie w <xref:System.Xml.XmlWriter> celu wypełnienia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="850a2-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="850a2-118">Jednak najbardziej typowym sposobem tworzenia drzewa XML jest:</span><span class="sxs-lookup"><span data-stu-id="850a2-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="850a2-119">Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników zapytania LINQ do wypełnienia drzewa XML, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="850a2-119">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="850a2-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="850a2-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="850a2-121">Serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="850a2-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="850a2-122">Można serializować drzewo XML do <xref:System.IO.File> , a <xref:System.IO.TextWriter> lub <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="850a2-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="850a2-123">Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XML (Visual Basic)](serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-123">For more information, see [Serializing XML Trees (Visual Basic)](serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="850a2-124">Pobieranie danych XML za pomocą metod osi</span><span class="sxs-lookup"><span data-stu-id="850a2-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="850a2-125">Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="850a2-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="850a2-126">Zapytania LINQ działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania i przetwarzania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="850a2-126">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="850a2-127">Aby uzyskać więcej informacji, zobacz [LINQ to XML osi (Visual Basic)](linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-127">For more information, see [LINQ to XML Axes (Visual Basic)](linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="850a2-128">Tworzenie zapytań dotyczących drzew XML</span><span class="sxs-lookup"><span data-stu-id="850a2-128">Querying XML Trees</span></span>  
 <span data-ttu-id="850a2-129">Można napisać zapytania LINQ wyodrębniające dane z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="850a2-129">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="850a2-130">Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczących drzew XML (Visual Basic)](querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-130">For more information, see [Querying XML Trees (Visual Basic)](querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="850a2-131">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="850a2-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="850a2-132">Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty.</span><span class="sxs-lookup"><span data-stu-id="850a2-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="850a2-133">Można również usunąć element z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="850a2-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="850a2-134">Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="850a2-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850a2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="850a2-135">See also</span></span>

- [<span data-ttu-id="850a2-136">Omówienie programowania LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a2-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
