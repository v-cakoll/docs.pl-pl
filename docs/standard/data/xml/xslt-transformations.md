---
title: Przekształcenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 922de11567af9409265ee18bfa6a2637951c57c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571004"
---
# <a name="xslt-transformations"></a>Przekształcenia XSLT
Extensible Stylesheet Language Transformation (XSLT) pozwala na przekształcanie zawartości dokumentu XML źródła do innego dokumentu, która różni się w formacie lub struktury. Na przykład można użyć XSLT do transformacji XML w kodzie HTML do użytku w witrynie sieci Web lub aby przekształcić go do dokumentu, który zawiera tylko te pola, które są wymagane przez aplikację. Ten proces transformacji jest określona przez [zalecenie W3C transformacji XSL (XSLT) w wersji 1.0](https://www.w3.org/TR/xslt-10/).  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesorze XSLT w .NET. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy obsługuje [zalecenie W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).  
  
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
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
