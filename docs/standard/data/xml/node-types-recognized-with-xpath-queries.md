---
title: "Typy węzłów rozpoznany z kwerendy XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db309bf0d04dfab4fd9fbdd2c8b145c1705d8428
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a>Typy węzłów rozpoznany z kwerendy XPath
Typy węzłów rozpoznane w zapytaniu XPath nie są tego samego typy węzłów można odnaleźć w modelu DOM (Document Object).  
  
## <a name="w3c-xpath-node-types"></a>Typy węzłów XPath W3C  
 Typy węzłów rozpoznane w zapytaniu XPath nie są typy węzłów można odnaleźć w modelu DOM (Document Object). Poniżej przedstawiono typy węzłów XPath reprezentowany przez <xref:System.Xml.XPath.XPathNodeType> wyliczenia.  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Te typy węzłów są oparte na XPath modelu danych, gdzie węzły są uzyskiwane z zestawu XML informacji. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> i <xref:System.Xml.XPath.XPathNodeType.Whitespace> węzła typy rozszerzeń programu Microsoft .NET Framework do typów węzeł podstawowy opisanego w modelu danych XPath.  
  
 Typ węzła atrybutu służy inaczej w modelu danych XPath nie znajduje się w modelu DOM. W modelu danych XPath węzeł elementu ma zestaw związane z jego węzłów atrybutu i węzeł element jest elementem nadrzędnym każdego węzła atrybutu. Jednak w modelu DOM, węzeł elementu jest właścicielem i nie nadrzędnego. W obu modelach węzłów atrybutu i przestrzeni nazw nie są uznawane za węzłów podrzędnych węzła elementu.  
  
 Typ węzła przestrzeni nazw jest dodanie do modelu danych XPath i nie jest rozpoznanym typem węzeł modelu DOM.  
  
 Aby uzyskać więcej informacji na temat nawigacji elementu, atrybutu i przestrzeni nazw węzłów, zobacz [węzła ustawić nawigacji przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) i [atrybut i element Namespace węzła nawigacji przy użyciu XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tematy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
