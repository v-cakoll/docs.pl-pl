---
title: Przy użyciu drzewa XML (Visual Basic) transformacji XSLT
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: a013e042bcaab321d8a5596368c349f296240d0b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820168"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a>Przy użyciu drzewa XML (Visual Basic) transformacji XSLT
Można utworzyć drzewa XML, tworzenie <xref:System.Xml.XmlReader> z drzewa XML Utwórz nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> która będzie zapisywała do nowego dokumentu. Następnie możesz wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do przekształcania. Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.  
  
## <a name="example"></a>Przykład  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
