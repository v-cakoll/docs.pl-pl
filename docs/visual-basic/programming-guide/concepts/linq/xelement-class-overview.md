---
title: "Przegląd klasy XElement klasy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: decd7c4f805de0d23b091972ee95a323baf0b7d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="0e225-102">Przegląd klasy XElement klasy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e225-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="0e225-103"><xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e225-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="0e225-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="0e225-104">It represents an XML element.</span></span> <span data-ttu-id="0e225-105">Ta klasa służy do tworzenia elementów; zmienić zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; dodać atrybuty do elementu; lub serializacji zawartości elementu w postaci tekstu.</span><span class="sxs-lookup"><span data-stu-id="0e225-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="0e225-106">Możesz również może współdziałać z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="0e225-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="0e225-107">Funkcje klasy XElement</span><span class="sxs-lookup"><span data-stu-id="0e225-107">XElement Functionality</span></span>  
 <span data-ttu-id="0e225-108">W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="0e225-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="0e225-109">Konstruowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="0e225-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="0e225-110">Można utworzyć drzewa XML na różne sposoby, m.in. następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0e225-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="0e225-111">Można utworzyć drzewa XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0e225-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="0e225-112">Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="0e225-113">Może przeanalizować składni XML z różnych źródeł, takich jak <xref:System.IO.TextReader>, pliki tekstowe lub adres sieci Web (URL).</span><span class="sxs-lookup"><span data-stu-id="0e225-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="0e225-114">Aby uzyskać więcej informacji, zobacz [analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="0e225-115">Można użyć <xref:System.Xml.XmlReader> do wypełnienia drzewa.</span><span class="sxs-lookup"><span data-stu-id="0e225-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="0e225-116">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e225-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="0e225-117">Jeśli masz moduł, który może zapisać zawartości do <xref:System.Xml.XmlWriter>, można użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, Przekaż twórcę modułu, a następnie użyj zawartość, która jest zapisywany w <xref:System.Xml.XmlWriter> do wypełnienia drzewo składni XML.</span><span class="sxs-lookup"><span data-stu-id="0e225-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="0e225-118">Jednak najczęściej można utworzyć drzewa XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0e225-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="0e225-119">Innej często techniki tworzenia drzewo XML polega na użyciu wyniki [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnić drzewo XML, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0e225-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="0e225-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0e225-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="0e225-121">Serializacja XML drzewa</span><span class="sxs-lookup"><span data-stu-id="0e225-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="0e225-122">Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0e225-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="0e225-123">Aby uzyskać więcej informacji, zobacz [drzew serializacji XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="0e225-124">Pobieranie danych XML za pomocą metod osi</span><span class="sxs-lookup"><span data-stu-id="0e225-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="0e225-125">Można użyć metody osi można pobrać atrybutów, elementy podrzędne elementów podrzędnych i elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0e225-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="0e225-126">zapytania działać na osi metod i podać kilka sposobów elastycznym i wydajnym do nawigowania i przetwarzania drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="0e225-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="0e225-127">Aby uzyskać więcej informacji, zobacz [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="0e225-128">Wykonywanie zapytania drzewa XML</span><span class="sxs-lookup"><span data-stu-id="0e225-128">Querying XML Trees</span></span>  
 <span data-ttu-id="0e225-129">Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które wyodrębnić dane z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="0e225-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="0e225-130">Aby uzyskać więcej informacji, zobacz [zapytanie drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="0e225-131">Modyfikowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="0e225-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="0e225-132">Można zmodyfikować elementu na wiele sposobów, łącznie ze zmianą jego zawartości lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0e225-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="0e225-133">Można również usunąć element z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0e225-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="0e225-134">Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e225-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e225-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e225-135">See Also</span></span>  
 [<span data-ttu-id="0e225-136">LINQ do programowania w języku XML-Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e225-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
