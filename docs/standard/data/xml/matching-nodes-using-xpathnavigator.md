---
title: "Zgodne węzły użyciu klasy XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a51c358ecb50c94ccde9f86ba80fc8f0670f82d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a>Zgodne węzły użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodę, aby określić, czy węzeł zgodne wyrażenie XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda pobiera wyrażenie XPath jako dane wejściowe i zwraca <xref:System.Boolean> wskazująca, czy bieżący węzeł zgodne danego wyrażenia XPath lub podane skompilowanych <xref:System.Xml.XPath.XPathExpression> obiektu.  
  
## <a name="matching-nodes"></a>Zgodne węzły  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda zwraca `true` Jeśli określono wyrażenie XPath pasuje do bieżącego węzła. Na przykład w przykładzie poniżej <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metoda zwróci `true` Jeśli bieżący węzeł jest elementem `b`, a element `b` ma atrybut `c`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> — Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wybierz dane XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Ocena wyrażenia XPath użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Typy węzłów rozpoznany z kwerendy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Kwerendy XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Wyrażenia XPath skompilowanych](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
