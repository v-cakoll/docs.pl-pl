---
title: Przy użyciu drzewa XML (C#) transformacji XSLT
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 3fa850c0f09404da49b2963e980d15e1ed54316f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276477"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a>Przy użyciu drzewa XML (C#) transformacji XSLT
Można utworzyć drzewa XML, tworzenie <xref:System.Xml.XmlReader> z drzewa XML Utwórz nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> która będzie zapisywała do nowego dokumentu. Następnie możesz wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do przekształcania. Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.  
  
## <a name="example"></a>Przykład  
  
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
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transform and output the results to a writer.  
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

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>  
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>  
- [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
