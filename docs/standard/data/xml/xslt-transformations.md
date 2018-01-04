---
title: "Przekształcenia XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92d0688b86e6a95af46e09c21c1a8b3cdf66efc3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations"></a>Przekształcenia XSLT
Extensible Stylesheet Language Transformation (XSLT) pozwala na przekształcanie zawartości dokumentu XML źródła do innego dokumentu, która różni się w formacie lub struktury. Na przykład można użyć XSLT do transformacji XML w kodzie HTML do użytku w witrynie sieci Web lub aby przekształcić go do dokumentu, który zawiera tylko te pola, które są wymagane przez aplikację. Ten proces transformacji jest określona przez [zalecenie W3C transformacji XSL (XSLT) w wersji 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesorze XSLT w programie .NET Framework. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa obsługuje zalecenie W3C XSLT 1.0.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzałe w programie .NET Framework w wersji 2.0. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest implementacją nowego aparatu XSLT. Zawiera ulepszenia wydajności i nowe funkcje zabezpieczeń. Zalecaną praktyką jest utworzenie aplikacji XSLT przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Zawiera informacje na temat używania <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 W tym artykule omówiono sposób migracji kod z <xref:System.Xml.Xsl.XslTransform> klasy.  
  
 [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Zawiera informacje na temat używania kompilatora XSLT.  
  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Zawiera informacje na temat używania <xref:System.Xml.Xsl.XslTransform> klasy.  
  
 **Uwaga** <xref:System.Xml.Xsl.XslTransform> klasa jest przestarzała w wersji .NET Framework 2.0.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
