---
title: Rozpoznawanie XSLT zewnętrznych arkuszy stylów i dokumentów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e8afd8c22ca757141d2a7b556b115f8380e731
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583944"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Rozpoznawanie XSLT zewnętrznych arkuszy stylów i dokumentów
Istnieje kilka razy podczas przekształcania, gdy trzeba rozwiązać zasobów zewnętrznych.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 Istnieje kilka razy podczas przekształcania, gdy trzeba rozwiązać zasobów zewnętrznych:  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> zlokalizować zewnętrznym arkuszu stylów.  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> do rozwiązania `<xsl:include>` lub `<xsl:import>` elementy znalezione w arkuszu stylów.  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> do rozwiązania `document()` funkcji.  
  
## <a name="using-the-xmlresolver-class"></a>Używanie klasy element XmlResolver  
 Jeśli uwierzytelnianie jest wymagane do dostępu do zasobu sieciowego, należy użyć <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, które mają <xref:System.Xml.XmlResolver> parametr do przekazania <xref:System.Xml.XmlResolver> obiektu, który ma zbioru właściwości niezbędnych poświadczeń.  
  
 Jeśli masz niestandardowy <xref:System.Xml.XmlResolver> czy chcesz używać, lub jeśli musisz określić inne poświadczenia w poniższej tabeli wymieniono zadania wymagane w zależności od tego, kiedy zewnętrznego zasobu wymaga rozwiązania.  
  
|Jakie procesy wymaga rozpoznawania|Wymagane zadania|  
|--------------------------------------|-------------------|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> zlokalizować arkusza stylów.|Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver> Jeśli arkusz stylów znajduje się na zasób, który wymaga poświadczeń.|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozpoznać `<xsl:include>` lub `<xsl:import>`.|Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Jest używana do ładowania arkusze stylów, odwołuje się `import` lub `include` instrukcji. Jeśli przekażesz w `null`, zasoby zewnętrzne nie są rozpoznawane.|  
|Podczas przekształcania w celu rozwiązania `document()` funkcji.|Określ <xref:System.Xml.XmlResolver> podczas przekształcania przy użyciu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> argumentu.|  
  
 `document()` Funkcja pobiera inne zasoby XML z arkusza stylów, dodatkowo do początkowy danych XML, dostarczanych przez strumień wejściowy. Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą być zlokalizowany w innym miejscu, <xref:System.Xml.XmlResolver> z `null` wartość dostarczona do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody `document()` funkcji z wykonywania. Jeśli chcesz używać `document()` funkcji, należy użyć <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, która przyjmuje <xref:System.Xml.XmlResolver> jako parametru, oprócz odpowiednich uprawnień zestawu.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XslTransform.Load%2A> metody i sposobu korzystania z <xref:System.Xml.XmlResolver>, zobacz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest wywoływana, uprawnienia są obliczane względem dowody dostarczone w czasie ładowania i przypisana do procesu przekształcenia cały zestaw uprawnień. Jeśli `document()` funkcja polegające na zainicjowanie akcji, która wymaga uprawnień nie można odnaleźć w zestawie, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [Dane wyjściowe klasy XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
- [Przekształcenia XSLT w różnych magazynach](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
- [Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
- [XSLT skryptów przy użyciu arkusza stylów \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
- [Obsługa funkcji msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
