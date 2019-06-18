---
title: Zestawy węzłów w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8160ec37f097b688aa4263a442c08a031f2bfc0c
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170793"
---
# <a name="node-sets-in-transformations"></a>Zestawy węzłów w przekształceniach
Węzeł zestawy są zestawu obejmującego cztery typy danych podstawowych, które są zwracane z wyrażeniami języka ścieżki XML (XPath). Zestaw węzłów, który jest nieuporządkowanej kolekcji węzłów bez duplikatów, utworzone w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w programie .NET Framework 2.0. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Węzeł zestawy są zestawu obejmującego cztery typy danych podstawowych, które są zwracane z wyrażenia XPath. Zestaw węzłów, który jest nieuporządkowanej kolekcji węzłów bez duplikatów, utworzone w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów. Zestawu węzłów, który jest wynikiem użyte w wyrażenie XPath `select` atrybutu w transformacji, ma takie samo zachowanie jako węzeł zestawu z XML Document Object Model (DOM). Możesz przejść węzłem, korzystając z zestawu metod pokazano w [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), w przeciwieństwie do wynikowego fragmentu drzewa lub wynikowego fragmentu drzewa, która używa <xref:System.Xml.XPath.XPathNodeIterator> nawigacji.  
  
 Poniższy przykładowy kod przedstawia sposób iterowania przez zestaw węzłów, gdy `variable` lub `parameter` elementu w arkuszu stylów zwróci zestawu węzłów.  
  
## <a name="style-sheet"></a>Arkusz stylów  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Dane wejściowe  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
