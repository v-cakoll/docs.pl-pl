---
title: Serializacja na element XmlReader (wywoływanie XSLT) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 05754593f4f30683ffabecaa8e16c35bf836a3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="a0208-102">Serializacja na element XmlReader (wywoływanie XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0208-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="a0208-103">Jeśli używasz <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można użyć <xref:System.Xml.Linq.XNode.CreateReader%2A> do utworzenia <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a0208-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a0208-104">Moduł odczytujący tego <xref:System.Xml.XmlReader> odczytuje węzły drzewa XML i odpowiednio je przetwarza.</span><span class="sxs-lookup"><span data-stu-id="a0208-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="a0208-105">Wywoływanie transformacji XSLT</span><span class="sxs-lookup"><span data-stu-id="a0208-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="a0208-106">Jedno możliwe użycie tej metody jest wywoływanie transformację XSLT.</span><span class="sxs-lookup"><span data-stu-id="a0208-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="a0208-107">Można utworzyć drzewa XML, Utwórz <xref:System.Xml.XmlReader> z drzewa XML, Utwórz nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> zapis do nowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a0208-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="a0208-108">Następnie można wywołać przekształcenia XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a0208-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a0208-109">Po pomyślnym zakończeniu transformacja, nowe drzewo XML jest wypełniana wyniki przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="a0208-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
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
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="a0208-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a0208-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0208-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0208-111">See Also</span></span>  
 [<span data-ttu-id="a0208-112">Serializacja drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0208-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
