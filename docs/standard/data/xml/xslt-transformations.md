---
title: Przekształcenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 92d0af1519260d458d3954beaef38e698142367a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288306"
---
# <a name="xslt-transformations"></a>Przekształcenia XSLT
Extensible Stylesheet Language Transformation (XSLT) umożliwia przekształcanie zawartości źródłowego dokumentu XML w inny dokument, który jest inny niż format lub struktura. Na przykład można użyć XSLT do przekształcenia XML w HTML do użycia w witrynie sieci Web lub przekształcenia go w dokument zawierający tylko pola wymagane przez aplikację. Ten proces transformacji jest określany na podstawie [zalecenia 1,0 w formacie W3C XSL Transformation (XSLT)](https://www.w3.org/TR/xslt-10/).  
  
 <xref:System.Xml.Xsl.XslCompiledTransform>Klasa to procesor XSLT w środowisku .NET. <xref:System.Xml.Xsl.XslCompiledTransform>Klasa obsługuje zalecenie dotyczące [W3C XSLT 1,0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework w wersji 2,0. <xref:System.Xml.Xsl.XslCompiledTransform>Klasa jest nową implementacją aparatu XSLT. Obejmuje to ulepszenia wydajności i nowe funkcje zabezpieczeń. Zalecanym sposobem jest utworzenie aplikacji XSLT przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md)  
 Zawiera informacje o korzystaniu z <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md)  
 W tym artykule omówiono sposób migrowania kodu z <xref:System.Xml.Xsl.XslTransform> klasy.  
  
 [Kompilator XSLT (xsltc.exe)](xslt-compiler-xsltc-exe.md)  
 Zawiera informacje o korzystaniu z kompilatora XSLT.  
  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)  
 Zawiera informacje o korzystaniu z <xref:System.Xml.Xsl.XslTransform> klasy.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](index.md)
