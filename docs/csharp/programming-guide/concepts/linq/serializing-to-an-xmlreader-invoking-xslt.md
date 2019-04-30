---
title: Serializowanie do elementu XmlReader (wywoływanie XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: 7faf86badad116d9e6ea920d9d745261c078c43c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680860"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="7f8ab-102">Serializowanie do elementu XmlReader (wywoływanie XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="7f8ab-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="7f8ab-103">Kiedy używasz <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz użyć <xref:System.Xml.Linq.XNode.CreateReader%2A> utworzyć <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7f8ab-104">Moduł odczytujący z tego <xref:System.Xml.XmlReader> odczytuje węzłów z drzewa XML i przetwarza je, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="7f8ab-105">Wywoływanie transformacji XSLT</span><span class="sxs-lookup"><span data-stu-id="7f8ab-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="7f8ab-106">Jedno możliwe użycie tej metody jest wywoływanie transformacji XSLT.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="7f8ab-107">Można utworzyć drzewa XML, tworzenie <xref:System.Xml.XmlReader> z drzewa XML, należy utworzyć nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> do zapisu do nowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="7f8ab-108">Następnie możesz wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="7f8ab-109">Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="7f8ab-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="7f8ab-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7f8ab-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f8ab-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f8ab-111">See also</span></span>

- [<span data-ttu-id="7f8ab-112">Serializowanie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7f8ab-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
