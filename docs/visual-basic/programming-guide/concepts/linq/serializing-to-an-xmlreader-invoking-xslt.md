---
title: Serializowanie do elementu XmlReader (wywoływanie transformacji XSLT)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: e51bfc031ad6d5d0eb98718f5d547fb18eb45295
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357377"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Serializacja do elementu XmlReader (wywołującego XSLT) (Visual Basic)
W przypadku korzystania z <xref:System.Xml?displayProperty=nameWithType> funkcji współdziałania programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można użyć programu <xref:System.Xml.Linq.XNode.CreateReader%2A> do utworzenia <xref:System.Xml.XmlReader> . Moduł odczytujący z tego <xref:System.Xml.XmlReader> odczytuje węzły z drzewa XML i przetwarza je odpowiednio.  
  
## <a name="invoking-an-xslt-transformation"></a>Wywoływanie transformacji XSLT  
 Jedynym możliwym zastosowaniem tej metody jest wywoływanie transformacji XSLT. Można utworzyć drzewo XML, utworzyć obiekt <xref:System.Xml.XmlReader> z drzewa XML, utworzyć nowy dokument, a następnie utworzyć <xref:System.Xml.XmlWriter> do zapisu w nowym dokumencie. Następnie można wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> . Po pomyślnym zakończeniu przekształcenia nowe drzewo XML zostanie wypełnione wynikami transformacji.  
  
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

- [Serializowanie drzew XML (Visual Basic)](serializing-xml-trees.md)
