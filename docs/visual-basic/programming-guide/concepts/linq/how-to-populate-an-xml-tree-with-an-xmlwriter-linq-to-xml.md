---
title: 'Jak: Wypełnić drzewo XML za pomocą XmlWriter (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: fecf57eac570a9ca57dd1fe2f7a0b54cd78c33b5
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267005"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Jak: Wypełnić drzewo XML za pomocą XmlWriter (LINQ do XML) (Visual Basic)
Jednym ze sposobów zapełnienia drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia <xref:System.Xml.XmlWriter>programu , a następnie zapisania w pliku <xref:System.Xml.XmlWriter>. Drzewo XML jest wypełniane wszystkimi węzłami, <xref:System.Xml.XmlWriter>które są zapisywane w pliku .  
  
 Zazwyczaj tej metody należy używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podczas korzystania z innej klasy, <xref:System.Xml.XmlWriter>która <xref:System.Xml.Xsl.XslCompiledTransform>spodziewa się napisać do , takich jak .  
  
## <a name="example"></a>Przykład  
 Jednym z <xref:System.Xml.Linq.XContainer.CreateWriter%2A> możliwych zastosowań jest podczas wywoływania transformacji XSLT. W tym przykładzie tworzy drzewo <xref:System.Xml.XmlReader> XML, tworzy z drzewa XML, <xref:System.Xml.XmlWriter> tworzy nowy dokument, a następnie tworzy do zapisu w nowym dokumencie. Następnie wywołuje transformację XSLT, <xref:System.Xml.XmlReader> przekazywanie i <xref:System.Xml.XmlWriter>. Po pomyślnym zakończeniu transformacji nowe drzewo XML jest wypełniane wynikami transformacji.  
  
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
- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
