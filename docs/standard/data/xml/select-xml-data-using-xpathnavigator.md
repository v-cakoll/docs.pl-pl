---
title: Wybieranie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d5e7074fc8c68a0a0243ea4ad237e713e0a729b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289060"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Wybieranie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Klasa zawiera zestaw metod służących do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub przy użyciu wyrażenia XPath. Po wybraniu można wykonać iterację w wybranym zestawie węzłów.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody wyboru XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera zestaw metod służących do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub przy użyciu wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator>Klasa udostępnia również zestaw zoptymalizowanych metod do wybierania obiektów nadrzędnych, podrzędnych i podrzędnych szybciej niż przy użyciu wyrażenia XPath. Wybrany zestaw węzłów jest zwracany w <xref:System.Xml.XPath.XPathNodeIterator> obiekcie lub <xref:System.Xml.XPath.XPathNavigator> obiekcie w przypadku pojedynczego wybranego węzła.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Wybieranie węzłów przy użyciu wyrażeń XPath  
 Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, należy użyć jednej z następujących metod wyboru.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Po wywołaniu te metody zwracają zestaw węzłów, które można swobodnie nawigować przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.  
  
 Nawigowanie przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu nie ma wpływu na pozycję obiektu, który <xref:System.Xml.XPath.XPathNavigator> został użyty do jego utworzenia. <xref:System.Xml.XPath.XPathNavigator>Obiekt zwrócony z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metod jest umieszczony w pojedynczym zwracanym węźle, a także nie ma wpływu na pozycję obiektu, który został <xref:System.Xml.XPath.XPathNavigator> użyty do jego utworzenia.  
  
 W poniższym przykładzie pokazano tworzenie <xref:System.Xml.XPath.XPathNavigator> obiektu z <xref:System.Xml.XPath.XPathDocument> obiektu, użycie <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody w celu wybrania węzłów w <xref:System.Xml.XPath.XPathDocument> obiekcie i użycie <xref:System.Xml.XPath.XPathNodeIterator> obiektu do iteracji w wybranych węzłach.  
  
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
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> , i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> <xref:System.Xml.XPath.XPathNavigator> klasy reprezentują wyrażenia XPath często używane do pobierania węzłów podrzędnych, podrzędnych i nadrzędnych. Te metody są zoptymalizowane pod kątem wydajności i są szybsze niż odpowiednie wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> , i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> wybierają węzły nadrzędne, podrzędne i podrzędne na podstawie <xref:System.Xml.XPath.XPathNodeType> wartości lub nazwy lokalnej i identyfikatora URI przestrzeni nazw węzłów do wybrania. Wybrane węzły nadrzędne, podrzędne i podrzędne są zwracane w <xref:System.Xml.XPath.XPathNodeIterator> obiekcie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](compiled-xpath-expressions.md)
