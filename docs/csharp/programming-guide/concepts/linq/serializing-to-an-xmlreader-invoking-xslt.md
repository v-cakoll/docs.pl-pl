---
title: Serializowanie do elementu XmlReader (wywoływanie XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: 7faf86badad116d9e6ea920d9d745261c078c43c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596959"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Serializowanie do elementu XmlReader (wywoływanie XSLT) (C#)
Kiedy używasz <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz użyć <xref:System.Xml.Linq.XNode.CreateReader%2A> utworzyć <xref:System.Xml.XmlReader>. Moduł odczytujący z tego <xref:System.Xml.XmlReader> odczytuje węzłów z drzewa XML i przetwarza je, odpowiednio.  
  
## <a name="invoking-an-xslt-transformation"></a>Wywoływanie transformacji XSLT  
 Jedno możliwe użycie tej metody jest wywoływanie transformacji XSLT. Można utworzyć drzewa XML, tworzenie <xref:System.Xml.XmlReader> z drzewa XML, należy utworzyć nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> do zapisu do nowego dokumentu. Następnie możesz wywołać transformację XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. Po pomyślnym ukończeniu przekształcenie nowego drzewa XML jest wypełniana wyniki przekształcenia.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Serializowanie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
