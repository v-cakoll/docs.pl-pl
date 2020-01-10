---
title: Przekształcenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 4bbecfbf1b163a9d7bfe6957806095b5b17fbab7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709637"
---
# <a name="xslt-transformations"></a>Przekształcenia XSLT
Extensible Stylesheet Language Transformation (XSLT) umożliwia przekształcanie zawartości źródłowego dokumentu XML w inny dokument, który jest inny niż format lub struktura. Na przykład można użyć XSLT do przekształcenia XML w HTML do użycia w witrynie sieci Web lub przekształcenia go w dokument zawierający tylko pola wymagane przez aplikację. Ten proces transformacji jest określany na podstawie [zalecenia 1,0 w formacie W3C XSL Transformation (XSLT)](https://www.w3.org/TR/xslt-10/).  
  
 Klasa <xref:System.Xml.Xsl.XslCompiledTransform> to procesor XSLT w programie .NET. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> obsługuje [zalecenie W3C XSLT 1,0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework wersji 2,0. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> jest nową implementacją aparatu XSLT. Obejmuje to ulepszenia wydajności i nowe funkcje zabezpieczeń. Zalecanym sposobem jest utworzenie aplikacji XSLT przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Zawiera informacje o korzystaniu z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 W tym artykule omówiono sposób migrowania kodu z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
 [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Zawiera informacje o korzystaniu z kompilatora XSLT.  
  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Zawiera informacje o korzystaniu z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
