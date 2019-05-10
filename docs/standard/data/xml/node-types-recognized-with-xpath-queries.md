---
title: Typy węzłów rozpoznawanych w zapytaniach XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa004f0def04c7efe2ba7450050a899760b0bbcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590179"
---
# <a name="node-types-recognized-with-xpath-queries"></a>Typy węzłów rozpoznawanych w zapytaniach XPath
Typy węzłów rozpoznawane w zapytaniu XPath nie są te same typy węzłów można odnaleźć w modelu DOM (Document Object).  
  
## <a name="w3c-xpath-node-types"></a>Typy węzłów XPath W3C  
 Typy węzłów rozpoznawane w zapytaniu XPath nie są typy węzłów, o których odnaleźć w modelu DOM (Document Object). Poniżej przedstawiono typy węzłów XPath, które są reprezentowane przez <xref:System.Xml.XPath.XPathNodeType> wyliczenia.  
  
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
  
 Te typy węzłów są oparte na modelu danych XPath, gdzie węzły są uzyskiwane z ustawić informacji XML. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> i <xref:System.Xml.XPath.XPathNodeType.Whitespace> typy węzłów są rozszerzeniami Microsoft .NET Framework do typów węzeł podstawowy opisane w modelu danych XPath.  
  
 Typ węzła atrybutu jest używana inaczej w modelu danych XPath niż w modelu DOM. W modelu danych XPath węzeł elementu zawiera zestaw węzłów atrybutu odnoszących się do niego, a węzeł elementu jest elementem nadrzędnym każdego węzła atrybutu. Jednak w modelu DOM, węzeł elementu jest właścicielem i nie nadrzędnym. W obu modelach węzłów atrybutu i przestrzeni nazw nie są uważane za węzły podrzędne węzła elementu.  
  
 Typ węzła obszaru nazw jest dodatkiem do modelu danych XPath i nie jest rozpoznawanym typem węzeł modelu DOM.  
  
 Aby uzyskać więcej informacji o nawigacji elementu, atrybutu i węzły przestrzeni nazw, zobacz [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) i [atrybut i klasy Namespace węzła nawigacji za pomocą XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tematy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
