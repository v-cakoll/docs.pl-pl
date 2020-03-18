---
title: Serializacja do czytnika XmlReader (wywoływania XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487182"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="9e9d6-102">Serializacja do czytnika XmlReader (wywoływania XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e9d6-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="9e9d6-103">Korzystając z <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można <xref:System.Xml.Linq.XNode.CreateReader%2A> użyć do <xref:System.Xml.XmlReader>utworzenia pliku .</span><span class="sxs-lookup"><span data-stu-id="9e9d6-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9e9d6-104">Moduł, który odczytuje z tego <xref:System.Xml.XmlReader> odczytuje węzły z drzewa XML i przetwarza je odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9e9d6-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="9e9d6-105">Wywoływanie transformacji XSLT</span><span class="sxs-lookup"><span data-stu-id="9e9d6-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="9e9d6-106">Jednym z możliwych użycia dla tej metody jest podczas wywoływania transformacji XSLT.</span><span class="sxs-lookup"><span data-stu-id="9e9d6-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="9e9d6-107">Można utworzyć drzewo XML, <xref:System.Xml.XmlReader> utworzyć drzewo z drzewa XML, utworzyć nowy <xref:System.Xml.XmlWriter> dokument, a następnie utworzyć do zapisania w nowym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9e9d6-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="9e9d6-108">Następnie można wywołać transformację XSLT, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>przekazując i .</span><span class="sxs-lookup"><span data-stu-id="9e9d6-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9e9d6-109">Po pomyślnym zakończeniu transformacji nowe drzewo XML jest wypełniane wynikami transformacji.</span><span class="sxs-lookup"><span data-stu-id="9e9d6-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="9e9d6-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9e9d6-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e9d6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e9d6-111">See also</span></span>

- [<span data-ttu-id="9e9d6-112">Serializujące drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9e9d6-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
