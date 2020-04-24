---
title: Rozpoznawanie zewnętrznych arkuszy stylów i dokumentów XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 504519532d9a6988209cf04fd6b6196796f929f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710300"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Rozpoznawanie zewnętrznych arkuszy stylów i dokumentów XSLT
Podczas transformacji może wystąpić kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 Podczas transformacji może wystąpić kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych:  
  
- W <xref:System.Xml.Xsl.XslTransform.Load%2A> celu zlokalizowania zewnętrznego arkusza stylów.  
  
- W <xref:System.Xml.Xsl.XslTransform.Load%2A> celu rozpoznania `<xsl:include>` `<xsl:import>` elementów znalezionych w arkuszu stylów.  
  
- W <xref:System.Xml.Xsl.XslTransform.Transform%2A> celu rozwiązania wszelkich `document()` funkcji.  
  
## <a name="using-the-xmlresolver-class"></a>Korzystanie z klasy XmlResolver  
 Jeśli do uzyskania dostępu do zasobu sieciowego jest wymagane uwierzytelnianie, użyj <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które mają <xref:System.Xml.XmlResolver> parametr do przekazania <xref:System.Xml.XmlResolver> obiektu, który ma wymagane właściwości poświadczeń.  
  
 Jeśli masz niestandardowy <xref:System.Xml.XmlResolver> , którego chcesz użyć, lub jeśli chcesz określić inne poświadczenia, w poniższej tabeli wymieniono wymagane zadanie, w zależności od tego, kiedy zasób zewnętrzny wymaga rozwiązania.  
  
|Jaki proces wymaga rozwiązania|Zadanie wymagane|  
|--------------------------------------|-------------------|  
|W <xref:System.Xml.Xsl.XslTransform.Load%2A> celu zlokalizowania arkusza stylów.|Określ przeciążoną <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver> Jeśli arkusz stylów znajduje się na zasobie, który wymaga poświadczeń.|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozpoznawania `<xsl:include>` lub `<xsl:import>`.|Określ przeciążoną <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Służy do ładowania arkuszy stylów, do których odwołuje się `import` instrukcja `include` or. Jeśli przejdziesz `null`do programu, zasoby zewnętrzne nie zostaną rozwiązane.|  
|Podczas przekształcania w celu rozwiązania `document()` wszelkich funkcji.|Określ <xref:System.Xml.XmlResolver> podczas transformacji przy użyciu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> argument.|  
  
 `document()` Funkcja pobiera inne zasoby XML z arkusza stylów, oprócz początkowych danych XML dostarczonych przez strumień wejściowy. Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą znajdować się w <xref:System.Xml.XmlResolver> innym miejscu `null` , a wartość dostarczona do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody `document()` uniemożliwia wykonanie funkcji. Jeśli chcesz użyć `document()` funkcji, użyj <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> jako parametr, oprócz odpowiedniego zestawu uprawnień.  
  
 Aby uzyskać więcej informacji na <xref:System.Xml.Xsl.XslTransform.Load%2A> temat metody i jej używania <xref:System.Xml.XmlResolver>, zobacz. <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>  
  
 Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda jest wywoływana, uprawnienia są obliczane na podstawie dowodów dostarczonych w czasie ładowania, a zestaw uprawnień jest przypisany do całego procesu transformacji. Jeśli `document()` funkcja próbuje zainicjować akcję, która wymaga uprawnień nieznalezionych w zestawie, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz też

- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Dane wyjściowe klasy XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Przekształcenia XSLT w różnych magazynach](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Obsługa skryptów arkusza stylów \<XSLT przy użyciu msxsl:>skryptu](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [Obsługa funkcji msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
