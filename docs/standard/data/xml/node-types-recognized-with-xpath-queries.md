---
title: Typy węzłów rozpoznawanych w zapytaniach XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710547"
---
# <a name="node-types-recognized-with-xpath-queries"></a>Typy węzłów rozpoznawanych w zapytaniach XPath
Typy węzłów rozpoznawane w zapytaniu XPath nie są tymi samymi typami węzłów, które znajdują się w Document Object Model (DOM).  
  
## <a name="w3c-xpath-node-types"></a>Typy węzłów W3C XPath  
 Typy węzłów rozpoznawane w zapytaniu XPath nie są typami węzłów znalezionych w Document Object Model (DOM). Poniżej przedstawiono typy węzłów XPath reprezentowane przez <xref:System.Xml.XPath.XPathNodeType> Wyliczenie.  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Te typy węzłów są oparte na modelu danych XPath, w którym węzły pochodzą z zestawu informacji XML. Typy <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> węzłów <xref:System.Xml.XPath.XPathNodeType.Whitespace> i są Microsoft .NET rozszerzenia struktur do typów węzła podstawowego opisanego w modelu danych XPath.  
  
 Typ węzła atrybutu jest używany inaczej w modelu danych XPath, niż jest w modelu DOM. W modelu danych XPath węzeł elementu ma zestaw węzłów atrybutów związanych z nim, a węzeł elementu jest elementem nadrzędnym każdego węzła atrybutu. Jednak w modelu DOM węzeł elementu jest właścicielem, a nie elementem nadrzędnym. W obu modelach węzły atrybut i przestrzeń nazw nie są traktowane jako węzły podrzędne węzła elementu.  
  
 Typ węzła przestrzeni nazw jest dodatkiem do modelu danych XPath i nie jest rozpoznawanym typem węzła DOM.  
  
 Aby uzyskać więcej informacji na temat nawigowania po węzłach elementów, atrybutów i przestrzeni nazw, zobacz [Nawigacja zestawu węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) oraz [nawigowanie po atrybutach i węzłach przestrzeni nazw za pomocą obiektów XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
