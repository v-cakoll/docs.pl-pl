---
title: Dopasowywanie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 47b0ba7e705ad602825dcca3f24c207362174a4c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289125"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Dopasowywanie węzłów przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Klasa zapewnia metodę, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Aby określić, czy węzeł dopasowuje wyrażenie XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda przyjmuje wyrażenie XPath jako dane wejściowe i zwraca wartość <xref:System.Boolean> wskazującą, czy bieżący węzeł odpowiada danemu wyrażeniu XPath lub podanemu skompilowanemu <xref:System.Xml.XPath.XPathExpression> obiektowi.  
  
## <a name="matching-nodes"></a>Zgodne węzły  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda zwraca `true` Jeśli bieżący węzeł pasuje do określonego wyrażenia XPath. Na przykład w poniższym przykładzie kodu Metoda zwróci wartość, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> `true` Jeśli bieżącym węzłem jest element `b` , a element `b` ma atrybut `c` .  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator> .  
  
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
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](compiled-xpath-expressions.md)
