---
title: Przy użyciu drzewa XML (C#) transformacji XSLT
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 3fa850c0f09404da49b2963e980d15e1ed54316f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062341"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="8029d-102">Przy użyciu drzewa XML (C#) transformacji XSLT</span><span class="sxs-lookup"><span data-stu-id="8029d-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="8029d-103">Można utworzyć drzewa XML, tworzenie <xref:System.Xml.XmlReader> z drzewa XML Utwórz nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> która będzie zapisywała do nowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8029d-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="8029d-104">Następnie możesz wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do przekształcania.</span><span class="sxs-lookup"><span data-stu-id="8029d-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="8029d-105">Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="8029d-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8029d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8029d-106">Example</span></span>  
  
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
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="8029d-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8029d-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8029d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8029d-108">See Also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>  
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="8029d-109">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="8029d-109">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
