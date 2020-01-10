---
title: Wybieranie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710170"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Wybieranie danych XML przy użyciu klasy XPathNavigator
Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia zestaw metod służących do wybierania zestawu węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> za pomocą wyrażenia XPath. Po wybraniu można wykonać iterację w wybranym zestawie węzłów.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody wyboru XPathNavigator  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia zestaw metod służących do wybierania zestawu węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> za pomocą wyrażenia XPath. Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia również zestaw zoptymalizowanych metod do wybierania obiektów nadrzędnych, podrzędnych i podrzędnych szybciej niż przy użyciu wyrażenia XPath. Wybrany zestaw węzłów jest zwracany w obiekcie <xref:System.Xml.XPath.XPathNodeIterator> lub obiekcie <xref:System.Xml.XPath.XPathNavigator> w przypadku pojedynczego wybranego węzła.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Wybieranie węzłów przy użyciu wyrażeń XPath  
 Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, należy użyć jednej z następujących metod wyboru.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Po wywołaniu te metody zwracają zestaw węzłów, za pomocą których można swobodnie poruszać się przy użyciu obiektu <xref:System.Xml.XPath.XPathNodeIterator> lub obiektu <xref:System.Xml.XPath.XPathNavigator> w przypadku jednego wybranego węzła.  
  
 Nawigowanie przy użyciu obiektu <xref:System.Xml.XPath.XPathNodeIterator> nie wpływa na pozycję obiektu <xref:System.Xml.XPath.XPathNavigator>, który został użyty do jego utworzenia. Obiekt <xref:System.Xml.XPath.XPathNavigator> zwrócony z metod <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> jest umieszczony w pojedynczym zwracanym węźle, a także nie ma wpływu na pozycję obiektu <xref:System.Xml.XPath.XPathNavigator> użytego do jego utworzenia.  
  
 W poniższym przykładzie pokazano Tworzenie obiektu <xref:System.Xml.XPath.XPathNavigator> z obiektu <xref:System.Xml.XPath.XPathDocument>, użycie metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> do wybrania węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> i użycie obiektu <xref:System.Xml.XPath.XPathNodeIterator> do iteracji w wybranych węzłach.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 Przykład pobiera `books.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Zoptymalizowane metody zaznaczania  
 Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> klasy <xref:System.Xml.XPath.XPathNavigator> reprezentują wyrażenia XPath często używane do pobierania węzłów podrzędnych, podrzędnych i nadrzędnych. Te metody są zoptymalizowane pod kątem wydajności i są szybsze niż odpowiednie wyrażenia XPath. Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> wybierają węzły nadrzędne, podrzędne i podrzędne na podstawie wartości <xref:System.Xml.XPath.XPathNodeType> lub nazwy lokalnej oraz identyfikatora URI przestrzeni nazw węzłów do wybrania. Wybrane węzły nadrzędne, podrzędne i podrzędne są zwracane w obiekcie <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
