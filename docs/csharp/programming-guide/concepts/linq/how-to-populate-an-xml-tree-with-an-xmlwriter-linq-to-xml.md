---
title: Jak wypełnić drzewo XML xmlwriterem (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: f48843af403f2ee0e6d2850deab009a143f55dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345775"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Jak wypełnić drzewo XML xmlwriterem (LINQ do XML) (C#)
Jednym ze sposobów wypełnienia drzewa XML <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest <xref:System.Xml.XmlWriter>użycie do utworzenia <xref:System.Xml.XmlWriter>, a następnie zapis do . Drzewo XML jest wypełniane wszystkimi węzłami, <xref:System.Xml.XmlWriter>które są zapisywane w pliku .  
  
 Zazwyczaj należy użyć tej metody, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gdy używasz z inną klasą, <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform>która oczekuje, aby zapisać do , takich jak .  
  
## <a name="example"></a>Przykład  
 Jednym z <xref:System.Xml.Linq.XContainer.CreateWriter%2A> możliwych użycia jest podczas wywoływania transformacji XSLT. W tym przykładzie tworzy drzewo <xref:System.Xml.XmlReader> XML, tworzy z drzewa XML, tworzy <xref:System.Xml.XmlWriter> nowy dokument, a następnie tworzy do zapisania w nowym dokumencie. Następnie wywołuje transformację XSLT, <xref:System.Xml.XmlReader> przekazując i <xref:System.Xml.XmlWriter>. Po pomyślnym zakończeniu transformacji nowe drzewo XML jest wypełniane wynikami transformacji.  
  
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
