---
title: "Porady: wypełnianie drzewo XML z XmlWriter (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2df0626d0376973aeaa09876c6737c93dd671da4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Porady: wypełnianie drzewo XML z XmlWriter (LINQ do XML) (C#)
Jednym ze sposobów wypełniania drzewo XML jest użycie <xref:System.Xml.Linq.XContainer.CreateWriter%2A> utworzyć <xref:System.Xml.XmlWriter>, a następnie zapisać <xref:System.Xml.XmlWriter>. Drzewo składni XML jest wypełniana wszystkie węzły, które są zapisywane w <xref:System.Xml.XmlWriter>.  
  
 Ta metoda będzie zazwyczaj używana, gdy używasz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z innej klasy, która oczekuje do zapisu <xref:System.Xml.XmlWriter>, takich jak <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Przykład  
 Jedno możliwe użycie dla <xref:System.Xml.Linq.XContainer.CreateWriter%2A> jest wywoływanie transformację XSLT. W tym przykładzie tworzy drzewo XML, tworzy <xref:System.Xml.XmlReader> z drzewa XML tworzy nowy dokument, a następnie tworzy <xref:System.Xml.XmlWriter> zapis do nowego dokumentu. Następnie wywołuje przekształcenia XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. Po pomyślnym zakończeniu transformacja, nowe drzewo XML jest wypełniana wyniki przekształcenia.  
  
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
 [Tworzenie drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
