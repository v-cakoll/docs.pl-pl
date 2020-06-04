---
title: 'Instrukcje: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: b3a36326175eeba8cd692a2c71f1f9b0fde24b5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397976"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Instrukcje: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (Visual Basic)
Jednym ze sposobów wypełnienia drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia <xref:System.Xml.XmlWriter> , a następnie zapisanie w <xref:System.Xml.XmlWriter> . Drzewo XML jest wypełniane wszystkimi węzłami, które są zapisywane w <xref:System.Xml.XmlWriter> .  
  
 Ta metoda zazwyczaj jest używana w przypadku używania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z inną klasą, która oczekuje zapisu w, na przykład <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="example"></a>Przykład  
 Jednym z możliwych użycia dla programu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformacji XSLT. Ten przykład tworzy drzewo XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML, tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> do zapisu w nowym dokumencie. Następnie wywołuje transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> . Po pomyślnym zakończeniu przekształcenia nowe drzewo XML zostanie wypełnione wynikami transformacji.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md)
