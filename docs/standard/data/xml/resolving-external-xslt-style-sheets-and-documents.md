---
title: "Rozpoznawanie arkuszy stylów XSLT zewnętrznych i dokumentów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 85176c45b768d1e8fe9efc408fd644bf33aa8c05
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Rozpoznawanie arkuszy stylów XSLT zewnętrznych i dokumentów
Istnieje kilka razy podczas transformację, gdy trzeba rozwiązać zasobów zewnętrznych.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 Istnieje kilka razy podczas transformację, gdy trzeba rozwiązać zasobów zewnętrznych:  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> można znaleźć zewnętrznego arkusza stylów.  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> do rozwiązania `<xsl:include>` lub `<xsl:import>` elementy znalezione w arkuszu stylów.  
  
-   Podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> do rozwiązania `document()` funkcji.  
  
## <a name="using-the-xmlresolver-class"></a>Używanie klasy element XmlResolver  
 Jeśli wymagane jest uwierzytelnienie dostępu do zasobu sieciowego, użyj <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które mają <xref:System.Xml.XmlResolver> parametr do przekazania <xref:System.Xml.XmlResolver> obiektu, który ma wartość właściwości niezbędne poświadczenia.  
  
 Jeśli masz niestandardowego <xref:System.Xml.XmlResolver> czy ma być używany, lub jeśli chcesz określić inne poświadczenia w poniższej tabeli przedstawiono zadania wymagane w zależności od tego, gdy zasób zewnętrzny potrzebuje rozwiązania.  
  
|Jakie procesy wymaga rozpoznawania|Wymagane zadania|  
|--------------------------------------|-------------------|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> zlokalizować arkusza stylów.|Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver> Jeśli arkusz stylów znajduje się na zasobie, który wymaga poświadczeń.|  
|Podczas <xref:System.Xml.Xsl.XslTransform.Load%2A> rozwiązywać `<xsl:include>` lub `<xsl:import>`.|Określ przeciążone <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która przyjmuje jako parametr, <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Jest używana do załadowania arkusze stylów odwołuje się `import` lub `include` instrukcje. W przypadku przekazania w `null`, zasobów zewnętrznych nie są rozpoznawane.|  
|Podczas transformacji do rozwiązania `document()` funkcji.|Określ <xref:System.Xml.XmlResolver> podczas transformacji przy użyciu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody pobierającej <xref:System.Xml.XmlResolver> argumentu.|  
  
 `document()` Funkcja pobiera inne zasoby XML z arkusza stylów, oprócz początkowej danych XML udostępniane przez strumień wejściowy. Ponieważ ta funkcja umożliwia dołączenie danych XML, które mogą być zlokalizowany w innym miejscu, <xref:System.Xml.XmlResolver> z `null` wartość dostarczona do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda `document()` funkcję wykonywania. Jeśli chcesz użyć `document()` funkcji, należy użyć <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody pobierającej <xref:System.Xml.XmlResolver> jako parametru, oprócz odpowiednich uprawnień ustawić.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XslTransform.Load%2A> — metoda i jego użycie <xref:System.Xml.XmlResolver>, zobacz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest wywoływana, uprawnienia są obliczane względem dowodów w czasie ładowania i przypisane do procesu transformacji cały zestaw uprawnień. Jeśli `document()` funkcja próbuje zainicjować akcję, która wymaga uprawnienia nie można odnaleźć w zestawie, jest zgłaszany wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Dane wyjściowe klasy XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [Przekształcenia XSLT w różnych magazynach](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [XSLT skryptów przy użyciu arkusza stylów \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [Obsługa funkcji msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
