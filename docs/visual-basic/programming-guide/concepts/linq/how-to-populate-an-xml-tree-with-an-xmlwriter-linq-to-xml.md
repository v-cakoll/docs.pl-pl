---
title: 'Instrukcje: Wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: de020444950695e27b9d840dac41fab74b9c7eba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835431"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Instrukcje: Wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (Visual Basic)
Jednym ze sposobów wypełnianie drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> utworzyć <xref:System.Xml.XmlWriter>, a następnie zapisać <xref:System.Xml.XmlWriter>. Drzewa XML jest wypełniana przy użyciu wszystkie węzły, które są zapisywane w <xref:System.Xml.XmlWriter>.  
  
 Zazwyczaj używasz tej metody, gdy używasz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z innej klasy, który oczekuje, że do zapisu <xref:System.Xml.XmlWriter>, takich jak <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Przykład  
 Jeden możliwe na użytek <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformacji XSLT. W tym przykładzie tworzy drzewa XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> do zapisu do nowego dokumentu. Następnie wywołuje transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
