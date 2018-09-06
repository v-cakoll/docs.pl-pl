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
ms.openlocfilehash: 10aff89679d5c8099d5128540521879f10e3e294
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041200"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Dopasowywanie węzłów przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodę pozwala ustalić, czy węzeł odpowiada wyrażenie XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda przyjmuje wyrażenia XPath jako dane wejściowe i zwraca <xref:System.Boolean> oznacza to, czy bieżący węzeł odpowiada danemu wyrażeniu XPath lub podane skompilowanych <xref:System.Xml.XPath.XPathExpression> obiektu.  
  
## <a name="matching-nodes"></a>Dopasowywanie węzłów  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda zwraca `true` Jeśli wyrażenia XPath określonych pasuje do bieżącego węzła. Na przykład w poniższym przykładzie kodu <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metoda zwróci `true` Jeśli bieżącego węzła jest elementem `b`, a element `b` ma atrybut `c`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>.  
  
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
