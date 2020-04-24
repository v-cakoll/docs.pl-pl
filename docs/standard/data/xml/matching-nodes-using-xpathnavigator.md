---
title: Dopasowywanie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710690"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Dopasowywanie węzłów przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia metodę, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> aby określić, czy węzeł dopasowuje wyrażenie XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda przyjmuje wyrażenie XPath jako dane wejściowe i zwraca wartość wskazującą <xref:System.Boolean> , czy bieżący węzeł odpowiada danemu wyrażeniu XPath lub podanemu skompilowanemu <xref:System.Xml.XPath.XPathExpression> obiektowi.  
  
## <a name="matching-nodes"></a>Zgodne węzły  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda zwraca `true` Jeśli bieżący węzeł pasuje do określonego wyrażenia XPath. Na przykład w <xref:System.Xml.XPath.XPathNavigator.Matches%2A> poniższym przykładzie kodu Metoda zwróci wartość, `true` Jeśli bieżącym węzłem jest element `b`, a element `b` ma atrybut. `c`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>.  
  
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

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
