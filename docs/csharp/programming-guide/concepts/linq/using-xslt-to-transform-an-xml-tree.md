---
title: Przekształcanie drzewa XML () przy użyciuC#XSLT ()
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 7ebcfbd6be86fdd5e12bfc48a0fe80a084c6f9b5
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140910"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="288d8-102">Przekształcanie drzewa XML () przy użyciuC#XSLT ()</span><span class="sxs-lookup"><span data-stu-id="288d8-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="288d8-103">Można utworzyć drzewo XML, utworzyć <xref:System.Xml.XmlReader> z drzewa XML, utworzyć nowy dokument i utworzyć <xref:System.Xml.XmlWriter>, który będzie zapisywać w nowym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="288d8-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="288d8-104">Następnie można wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do transformacji.</span><span class="sxs-lookup"><span data-stu-id="288d8-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="288d8-105">Po pomyślnym zakończeniu przekształcenia nowe drzewo XML zostanie wypełnione wynikami transformacji.</span><span class="sxs-lookup"><span data-stu-id="288d8-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="288d8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="288d8-106">Example</span></span>  
  
```csharp  
string xslt = @"<?xml version='1.0'?>  
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
```  
  
 <span data-ttu-id="288d8-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="288d8-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="288d8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="288d8-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
