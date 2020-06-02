---
title: Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287808"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodę szacowania wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda przyjmuje wyrażenie XPath, szacuje go i zwraca typ W3C XPath o wartości logicznej, liczb, ciągu lub zestawu węzłów na podstawie wyniku wyrażenia XPath.  
  
## <a name="the-evaluate-method"></a>Metoda szacowania  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda przyjmuje wyrażenie XPath, oblicza go i zwraca wynik z typem Boolean ( <xref:System.Boolean> ), Number ( <xref:System.Double> ), String ( <xref:System.String> ) lub Set ( <xref:System.Xml.XPath.XPathNodeIterator> ). Na przykład <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda może być użyta w metodzie matematycznej. Poniższy przykładowy kod oblicza łączną cenę wszystkich ksiąg w `books.xml` pliku.  
  
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
  
 Przykład pobiera `books.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>Funkcja position i Last  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda jest przeciążona. Jedna z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod przyjmuje <xref:System.Xml.XPath.XPathNodeIterator> obiekt jako parametr. Ta konkretna <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda jest taka sama jak <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda, która przyjmuje tylko <xref:System.Xml.XPath.XPathExpression> obiekt jako parametr, z tą różnicą, że zezwala na argument zestawu węzłów, aby określić bieżący kontekst do przeprowadzenia oceny. Ten kontekst jest wymagany dla wyrażenia XPath `position()` i `last()` funkcji, ponieważ odnoszą się do bieżącego węzła kontekstu. O ile nie jest używany jako predykat w kroku lokalizacji, `position()` `last()` funkcje i wymagają odwołania do zestawu węzłów, aby można je było oszacować w przeciwnym razie `position` funkcje i `last` zwracają `0` .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](compiled-xpath-expressions.md)
