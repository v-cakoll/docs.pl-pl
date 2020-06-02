---
title: Rozpoznawanie zewnętrznych arkuszy stylów i dokumentów XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 8e7f66d67f2520b47c30307a98ed2f3fb08455df
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291477"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Rozpoznawanie zewnętrznych arkuszy stylów i dokumentów XSLT
Podczas transformacji może wystąpić kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
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
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozpoznawania `<xsl:include>` lub `<xsl:import>` .|Określ przeciążoną <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr <xref:System.Xml.XmlResolver> . <xref:System.Xml.XmlResolver>Służy do ładowania arkuszy stylów, do których odwołuje się `import` `include` instrukcja or. Jeśli przejdziesz do programu `null` , zasoby zewnętrzne nie zostaną rozwiązane.|  
|Podczas przekształcania w celu rozwiązania wszelkich `document()` funkcji.|Określ <xref:System.Xml.XmlResolver> podczas transformacji przy użyciu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> argument.|  
  
 `document()`Funkcja pobiera inne zasoby XML z arkusza stylów, oprócz początkowych danych XML dostarczonych przez strumień wejściowy. Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą znajdować się w innym miejscu, <xref:System.Xml.XmlResolver> a `null` wartość dostarczona do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody uniemożliwia `document()` wykonanie funkcji. Jeśli chcesz użyć `document()` funkcji, użyj <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> jako parametr, oprócz odpowiedniego zestawu uprawnień.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XslTransform.Load%2A> metody i jej używania <xref:System.Xml.XmlResolver> , zobacz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType> .  
  
 Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda jest wywoływana, uprawnienia są obliczane na podstawie dowodów dostarczonych w czasie ładowania, a zestaw uprawnień jest przypisany do całego procesu transformacji. Jeśli `document()` Funkcja próbuje zainicjować akcję, która wymaga uprawnień nieznalezionych w zestawie, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Dane wyjściowe klasy XslTransform](outputs-from-an-xsltransform.md)
- [Przekształcenia XSLT w różnych magazynach](xslt-transformations-over-different-stores.md)
- [Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Obsługa skryptów arkusza stylów XSLT przy użyciu\<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md)
- [Obsługa funkcji msxsl:node-set()](support-for-the-msxsl-node-set-function.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](xmldocument-input-to-xsltransform.md)
