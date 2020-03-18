---
title: Serializacja do czytnika XmlReader (wywoływania XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487182"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Serializacja do czytnika XmlReader (wywoływania XSLT) (C#)
Korzystając z <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można <xref:System.Xml.Linq.XNode.CreateReader%2A> użyć do <xref:System.Xml.XmlReader>utworzenia pliku . Moduł, który odczytuje z tego <xref:System.Xml.XmlReader> odczytuje węzły z drzewa XML i przetwarza je odpowiednio.  
  
## <a name="invoking-an-xslt-transformation"></a>Wywoływanie transformacji XSLT  
 Jednym z możliwych użycia dla tej metody jest podczas wywoływania transformacji XSLT. Można utworzyć drzewo XML, <xref:System.Xml.XmlReader> utworzyć drzewo z drzewa XML, utworzyć nowy <xref:System.Xml.XmlWriter> dokument, a następnie utworzyć do zapisania w nowym dokumencie. Następnie można wywołać transformację XSLT, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>przekazując i . Po pomyślnym zakończeniu transformacji nowe drzewo XML jest wypełniane wynikami transformacji.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Serializujące drzewa XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
