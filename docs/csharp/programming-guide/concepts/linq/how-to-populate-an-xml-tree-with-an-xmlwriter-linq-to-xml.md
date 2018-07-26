---
title: 'Porady: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198552"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Porady: wypełnianie drzewa XML elementem XmlWriter (LINQ to XML) (C#)
Jednym ze sposobów wypełnianie drzewa XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> utworzyć <xref:System.Xml.XmlWriter>, a następnie zapisać <xref:System.Xml.XmlWriter>. Drzewa XML jest wypełniana przy użyciu wszystkie węzły, które są zapisywane w <xref:System.Xml.XmlWriter>.  
  
 Zazwyczaj używasz tej metody, gdy używasz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z innej klasy, który oczekuje, że do zapisu <xref:System.Xml.XmlWriter>, takich jak <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Przykład  
 Jeden możliwe na użytek <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformacji XSLT. W tym przykładzie tworzy drzewa XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> do zapisu do nowego dokumentu. Następnie wywołuje transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.  
  
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
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
