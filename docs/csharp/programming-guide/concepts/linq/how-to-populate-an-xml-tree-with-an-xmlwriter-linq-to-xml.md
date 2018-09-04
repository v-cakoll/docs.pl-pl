---
title: 'Porady: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cd8f8b5c382c64e142d794951ea289a3ca979f81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530350"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="af16a-102">Porady: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af16a-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="af16a-103">Jednym ze sposobów wypełnianie drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> utworzyć <xref:System.Xml.XmlWriter>, a następnie zapisać <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="af16a-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="af16a-104">Drzewa XML jest wypełniana przy użyciu wszystkie węzły, które są zapisywane w <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="af16a-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="af16a-105">Zazwyczaj używasz tej metody, gdy używasz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z innej klasy, który oczekuje, że do zapisu <xref:System.Xml.XmlWriter>, takich jak <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="af16a-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af16a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="af16a-106">Example</span></span>  
 <span data-ttu-id="af16a-107">Jeden możliwe na użytek <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformacji XSLT.</span><span class="sxs-lookup"><span data-stu-id="af16a-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="af16a-108">W tym przykładzie tworzy drzewa XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> do zapisu do nowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="af16a-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="af16a-109">Następnie wywołuje transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="af16a-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="af16a-110">Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="af16a-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="af16a-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="af16a-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af16a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af16a-112">See Also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
- <xref:System.Xml.XmlWriter>  
- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [<span data-ttu-id="af16a-113">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="af16a-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
