---
title: Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2712c1de4a5f4a06ba041fdc0c5df2487eebdd2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519354"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody ocena wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda przyjmuje wyrażenia XPath, oblicza ona i zwraca typ W3C XPath atrybut typu wartość logiczna, liczba, ciąg lub zestaw węzłów na podstawie wyniku wyrażenia XPath.  
  
## <a name="the-evaluate-method"></a>Oceń — metoda  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda przyjmuje wyrażenia XPath, oblicza ona i zwraca wynik typizowaną wartość logiczna (<xref:System.Boolean>), liczba (<xref:System.Double>), ciąg (<xref:System.String>), lub zestaw węzłów (<xref:System.Xml.XPath.XPathNodeIterator>). Na przykład <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda może być użyta w metodzie matematyczne. Poniższy przykład kodu oblicza całkowita cena wszystkie książki w `books.xml` pliku.  
  
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
  
### <a name="position-and-last-functions"></a>położenie i ostatniej funkcji  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Jest przeciążona metoda. Jedną z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod przyjmuje <xref:System.Xml.XPath.XPathNodeIterator> obiektu jako parametr. Tej konkretnej <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody jest taka sama jak <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody, która przyjmuje tylko <xref:System.Xml.XPath.XPathExpression> obiektu jako parametru, z tą różnicą, że umożliwia argument do określania bieżącego kontekstu, aby wykonać obliczenie na zestaw węzłów. Ten kontekst jest wymagany dla wyrażenia XPath `position()` i `last()` funkcji, ponieważ są one względem bieżącego węzła kontekstu. O ile nie jest używana jako predykat w kroku lokalizacji `position()` i `last()` funkcje wymagają odwołania do węzła, ustaw umożliwia ocenienie w przeciwnym razie `position` i `last` funkcje zwracają `0`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
