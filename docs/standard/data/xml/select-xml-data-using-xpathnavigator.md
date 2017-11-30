---
title: "Wybierz dane XML przy użyciu parametrem XPathNavigator"
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
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f63f23b1a07fbe77e77598cd05dcd25ee8ec158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="select-xml-data-using-xpathnavigator"></a>Wybierz dane XML przy użyciu parametrem XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używany do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath. Po wybraniu można iteracja wybranego zestawu węzłów.  
  
## <a name="xpathnavigator-selection-methods"></a>Element XPathNavigator wybór metody  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używany do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia również zestaw metod zoptymalizowany do wybierania węzły nadrzędne, podrzędne i obiekt podrzędny szybciej niż przy użyciu wyrażenia XPath. Wybrany zestaw węzłów jest zwracany w <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Wybieranie węzłów za pomocą wyrażenia XPath  
 Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, użyj jednej z następujących metod zaznaczenia.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Po wywołaniu, te metody zwracają zestaw węzłów, które można przejść za darmo przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.  
  
 Nawigacja przy <xref:System.Xml.XPath.XPathNodeIterator> obiekt nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt używany do jej utworzenia. <xref:System.Xml.XPath.XPathNavigator> Obiektu zwróconego z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody znajduje się na jednym węźle zwrócony i nie dotyczy również pozycja <xref:System.Xml.XPath.XPathNavigator> obiekt używany do jej utworzenia.  
  
 W poniższym przykładzie pokazano tworzenie <xref:System.Xml.XPath.XPathNavigator> obiekt z <xref:System.Xml.XPath.XPathDocument> obiektu, użycie <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody, aby wybrać węzły w <xref:System.Xml.XPath.XPathDocument> obiektu, a także korzystanie z <xref:System.Xml.XPath.XPathNodeIterator> obiekt, aby przejść przez wybrane węzły.  
  
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
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy reprezentują wyrażenia XPath najczęściej używane do pobierania węzłów podrzędnych, podrzędnym i nadrzędnym. Te metody są zoptymalizowane pod kątem wydajności i szybsze niż ich odpowiedniego wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody wybiera nadrzędne, podrzędne i węzłów elementów podrzędnych na podstawie <xref:System.Xml.XPath.XPathNodeType> wartość lub lokalna nazwa i identyfikator URI węzłów, aby wybrać przestrzeni nazw. Wybranego elementu nadrzędnego, podrzędne i węzły podrzędne są zwracane w <xref:System.Xml.XPath.XPathNodeIterator> obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Ocena wyrażenia XPath użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Zgodne węzły użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Typy węzłów rozpoznany z kwerendy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Kwerendy XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Wyrażenia XPath skompilowanych](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
