---
title: "Ustawia węzeł w przekształcenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d6d2f5a68ce5cef9937edc136e52efcd5366df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="node-sets-in-transformations"></a>Ustawia węzeł w przekształcenia
Zestaw węzłów są jednym z cztery typy podstawowe dane, które zostaną zwrócone z wyrażenia XML Path Language (XPath). Zestaw węzłów, które nieuporządkowaną zbiór węzłów bez duplikatów, utworzony w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Zestaw węzłów są jednym z cztery typy podstawowe dane, które zostaną zwrócone z wyrażenia XPath. Zestaw węzłów, które nieuporządkowaną zbiór węzłów bez duplikatów, utworzony w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów. Tego zestawu węzłów jest wynikiem wyrażenia używane w XPath `select` atrybutu w transformację, zachowanie jest takie samo jako węzeł ustawić z XML modelu DOM (Document Object). Można przejść węzła ustawić przy użyciu zestawu metod przedstawiono w [węzła ustawić nawigacji przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), w odróżnieniu od wynikowego fragmentu drzewa lub wynikowego fragmentu drzewa, który używa <xref:System.Xml.XPath.XPathNodeIterator> nawigacji.  
  
 Poniższy przykładowy kod przedstawia sposób wykonania iteracji w węźle ustawiane podczas `variable` lub `parameter` elementu w arkuszu stylów ocenia się na zestaw węzłów.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Klasa XslTransform implementuje procesorze XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
