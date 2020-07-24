---
title: Jak wypełnić drzewo XML elementem XmlWriter (LINQ to XML) (C#)
description: Dowiedz się, w jaki sposób wypełnić drzewo XML przy użyciu funkcji do tworzenia elementu XmlWriter, a następnie pisać do XmlWriter w LINQ to XML w języku C#.
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 9639c5947583bccf4f8ba427fc8611e181ef1536
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104801"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Jak wypełnić drzewo XML elementem XmlWriter (LINQ to XML) (C#)
Jednym ze sposobów wypełnienia drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia <xref:System.Xml.XmlWriter> , a następnie zapisanie w <xref:System.Xml.XmlWriter> . Drzewo XML jest wypełniane wszystkimi węzłami, które są zapisywane w <xref:System.Xml.XmlWriter> .  
  
 Ta metoda zazwyczaj jest używana w przypadku używania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z inną klasą, która oczekuje zapisu w, na przykład <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="example"></a>Przykład  
 Jednym z możliwych użycia dla programu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformacji XSLT. Ten przykład tworzy drzewo XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML, tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> do zapisu w nowym dokumencie. Następnie wywołuje transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> . Po pomyślnym zakończeniu przekształcenia nowe drzewo XML zostanie wypełnione wynikami transformacji.  
  
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
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
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
- [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md)
