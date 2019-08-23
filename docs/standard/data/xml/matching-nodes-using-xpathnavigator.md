---
title: Dopasowywanie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923329"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Dopasowywanie węzłów przy użyciu klasy XPathNavigator
Klasa zapewnia metodę, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> aby określić, czy węzeł dopasowuje wyrażenie XPath. <xref:System.Xml.XPath.XPathNavigator> Metoda przyjmuje wyrażenie XPath jako dane wejściowe i <xref:System.Boolean> zwraca wartość wskazującą, czy bieżący węzeł odpowiada danemu wyrażeniu XPath lub podanemu skompilowanemu <xref:System.Xml.XPath.XPathExpression> obiektowi. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
## <a name="matching-nodes"></a>Zgodne węzły  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda zwraca`true` Jeśli bieżący węzeł pasuje do określonego wyrażenia XPath. Na <xref:System.Xml.XPath.XPathNavigator.Matches%2A> przykład w poniższym przykładzie kodu Metoda `true` zwróci wartość, jeśli bieżącym węzłem jest element `b`, a element `b` ma atrybut `c`.  
  
> [!NOTE]
> Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
