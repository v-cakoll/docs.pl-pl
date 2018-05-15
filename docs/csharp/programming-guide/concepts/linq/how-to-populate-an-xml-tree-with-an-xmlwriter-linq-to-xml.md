---
title: 'Porady: wypełnianie drzewo XML z XmlWriter (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="9c7e5-102">Porady: wypełnianie drzewo XML z XmlWriter (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9c7e5-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9c7e5-103">Jednym ze sposobów wypełniania drzewo XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> utworzyć <xref:System.Xml.XmlWriter>, a następnie zapisać <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9c7e5-104">Drzewo składni XML jest wypełniana wszystkie węzły, które są zapisywane w <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="9c7e5-105">Ta metoda będzie zazwyczaj używana, gdy używasz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z innej klasy, która oczekuje do zapisu <xref:System.Xml.XmlWriter>, takich jak <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c7e5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c7e5-106">Example</span></span>  
 <span data-ttu-id="9c7e5-107">Jedno możliwe użycie dla <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformację XSLT.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="9c7e5-108">W tym przykładzie tworzy drzewo XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> zapis do nowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="9c7e5-109">Następnie wywołuje przekształcenia XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9c7e5-110">Po pomyślnym zakończeniu transformacja, nowe drzewo XML jest wypełniana wyniki przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="9c7e5-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="9c7e5-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c7e5-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c7e5-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c7e5-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="9c7e5-113">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9c7e5-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
