---
title: "Ocena wyrażenia XPath użyciu klasy XPathNavigator"
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
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d4515b8ebea338a153319dfd02eab8d389b843b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Ocena wyrażenia XPath użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody można oszacować wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> — Metoda przyjmuje wyrażenie XPath, oblicza ona i zwraca W3C XPath typu Boolean, numer, ciągu lub zestawu węzłów na podstawie wyniku wyrażenia XPath.  
  
## <a name="the-evaluate-method"></a>Ocena — metoda  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda pobiera wyrażenie XPath, oblicza ona i zwraca wynik typu Boolean (<xref:System.Boolean>), liczba (<xref:System.Double>), ciąg (<xref:System.String>), lub zestawu węzłów (<xref:System.Xml.XPath.XPathNodeIterator>). Na przykład <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda może być użyta w metodzie matematycznych. Poniższy przykładowy kod oblicza cena razem wszystkich książek w `books.xml` pliku.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 Przykład przyjmuje `books.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>pozycja i ostatniej funkcji  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metody jest przeciążona. Jeden z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ma metody <xref:System.Xml.XPath.XPathNodeIterator> obiektu jako parametr. Tego określonego <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda jest taki sam jak <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody pobierającej tylko <xref:System.Xml.XPath.XPathExpression> obiekt jako parametru, z wyjątkiem tego, aby umożliwiała węzła, ustaw argument do określenia bieżącego kontekstu podczas obliczania. Ten kontekst jest wymagany dla wyrażenia XPath `position()` i `last()` działa, ponieważ są one względem bieżącego węzła kontekstu. O ile nie jest używana jako predykat w kroku lokalizacji `position()` i `last()` funkcji wymaga odwołania do węzła, aby przyjąć w przeciwnym razie `position` i `last` funkcje zwracają `0`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
