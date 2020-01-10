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
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 Podczas transformacji może wystąpić kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych:  
  
- W <xref:System.Xml.Xsl.XslTransform.Load%2A>, aby zlokalizować zewnętrzny arkusz stylów.  
  
- Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozpoznawania elementów `<xsl:include>` lub `<xsl:import>` znalezionych w arkuszu stylów.  
  
- Podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> rozpoznawania jakichkolwiek funkcji `document()`.  
  
## <a name="using-the-xmlresolver-class"></a>Korzystanie z klasy XmlResolver  
 Jeśli do uzyskania dostępu do zasobu sieciowego jest wymagane uwierzytelnianie, użyj metod <xref:System.Xml.Xsl.XslTransform.Load%2A>, które mają parametr <xref:System.Xml.XmlResolver>, aby przekazać obiekt <xref:System.Xml.XmlResolver>, który ma wymagane właściwości poświadczeń.  
  
 Jeśli masz niestandardowy <xref:System.Xml.XmlResolver>, którego chcesz użyć, lub jeśli chcesz określić inne poświadczenia, Poniższa tabela zawiera listę zadań wymaganych w zależności od tego, kiedy zasób zewnętrzny wymaga rozwiązania.  
  
|Jaki proces wymaga rozwiązania|Zadanie wymagane|  
|--------------------------------------|-------------------|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> zlokalizować arkusz stylów.|Określ przeciążoną metodę <xref:System.Xml.Xsl.XslTransform.Load%2A>, która przyjmuje jako parametr <xref:System.Xml.XmlResolver>, jeśli arkusz stylów znajduje się na zasobie, który wymaga poświadczeń.|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozpoznawania `<xsl:include>` lub `<xsl:import>`.|Określ przeciążoną metodę <xref:System.Xml.Xsl.XslTransform.Load%2A>, która przyjmuje jako parametr <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> służy do ładowania arkuszy stylów, do których odwołuje się instrukcje `import` lub `include`. W przypadku przekazania `null`zasoby zewnętrzne nie zostaną rozwiązane.|  
|Podczas przekształcania, aby rozwiązać wszelkie `document()` funkcje.|Określ <xref:System.Xml.XmlResolver> podczas transformacji przy użyciu metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, która przyjmuje argument <xref:System.Xml.XmlResolver>.|  
  
 Funkcja `document()` pobiera inne zasoby XML z arkusza stylów, oprócz początkowych danych XML dostarczonych przez strumień wejściowy. Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą znajdować się w innym miejscu, <xref:System.Xml.XmlResolver> z `null` wartością dostarczoną do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> uniemożliwia wykonywanie funkcji `document()`. Jeśli chcesz użyć funkcji `document()`, użyj metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, która pobiera <xref:System.Xml.XmlResolver> jako parametr, oprócz posiadania odpowiedniego zestawu uprawnień.  
  
 Aby uzyskać więcej informacji na temat metody <xref:System.Xml.Xsl.XslTransform.Load%2A> i jej używania <xref:System.Xml.XmlResolver>, zobacz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Po wywołaniu metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> uprawnienia są obliczane na podstawie dowodów dostarczonych w czasie ładowania, a zestaw uprawnień jest przypisany do całego procesu transformacji. Jeśli funkcja `document()` próbuje zainicjować akcję, która wymaga uprawnień nieznalezionych w zestawie, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Dane wyjściowe klasy XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Przekształcenia XSLT w różnych magazynach](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Obsługa skryptów arkusza stylów XSLT przy użyciu \<msxsl: skrypt >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [Obsługa funkcji msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
