---
title: 'Obsługa msxsl: node-set() — funkcja'
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4b1fb4abe8ca0ba7afcefe996de59ceaf67a249
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252782"
---
# <a name="support-for-the-msxslnode-set-function"></a>Obsługa msxsl: node-set() — funkcja
`msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa w zestawie węzłów. Węzeł wynikowy ustawić opcji zawsze zawiera jeden węzeł i węzeł główny drzewa.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 `msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa w zestawie węzłów. Węzeł wynikowy ustawić opcji zawsze zawiera jeden węzeł i węzeł główny drzewa.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `$var` to zmienna, która jest węzeł drzewa w arkuszu stylów. Dla każdej instrukcji w połączeniu z `node-set` funkcja zezwala użytkownikowi na iterację w tym węźle drzewa jako zestaw węzłów.  
  
## <a name="nodesetxsl"></a>NodeSet.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Dane wyjściowe  
 Dane wyjściowe transformacji  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
