---
title: Wybieranie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177409"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Wybieranie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, używany do wybierania zestaw węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath. Po wybraniu, można wykonać iterację przez wybrany zestaw węzłów.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody wyboru klasy XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, używany do wybierania zestaw węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia także zestaw zoptymalizowanych metod szybciej niż przy użyciu wyrażenie XPath wybierania węzłów nadrzędnych i podrzędnych obiekt podrzędny. Wybrany zestaw węzłów jest zwracany w <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Wybieranie węzłów za pomocą wyrażenia XPath  
 Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, użyj jednej z następujących metod zaznaczenia.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Gdy zostanie wywołana, te metody zwracają zestaw węzłów, które możesz przejść za darmo przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.  
  
 Nawigacja przy <xref:System.Xml.XPath.XPathNodeIterator> obiekt nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt użyty do jego utworzenia. <xref:System.Xml.XPath.XPathNavigator> Obiekt zwracany z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metod znajduje się w pojedynczym węźle zwracane i również nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt użyty do jego utworzenia.  
  
 W poniższym przykładzie pokazano tworzenie <xref:System.Xml.XPath.XPathNavigator> obiektu z <xref:System.Xml.XPath.XPathDocument> obiektu, korzystanie z <xref:System.Xml.XPath.XPathNavigator.Select%2A> metodę, aby wybrać węzły w <xref:System.Xml.XPath.XPathDocument> obiektu, a także korzystanie z <xref:System.Xml.XPath.XPathNodeIterator> obiektu do wykonywania iteracji wybranych węzłów.  
  
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
  
 Przykład przyjmuje `books.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Zoptymalizowane metody  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy reprezentują wyrażenia XPath, które często używane do pobierania węzłów podrzędnych, obiekt podrzędny i nadrzędny. Te metody są zoptymalizowane pod kątem wydajności i są szybsze niż ich odpowiednich wyrażeń XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody wybiera elementu nadrzędnego, podrzędnego i węzłów podrzędnych, na podstawie <xref:System.Xml.XPath.XPathNodeType> wartość lub lokalna nazwa i identyfikator URI węzłów, aby wybrać przestrzeni nazw. Wybranego elementu nadrzędnego, podrzędnego i węzły podrzędne, które są zwracane w <xref:System.Xml.XPath.XPathNodeIterator> obiektu.  
  
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
