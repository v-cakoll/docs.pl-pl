---
title: Skompilowane wyrażenia XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: b4675765849299050eb6cddeaaa497bc6cdc620a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711106"
---
# <a name="compiled-xpath-expressions"></a>Skompilowane wyrażenia XPath
Obiekt <xref:System.Xml.XPath.XPathExpression> reprezentuje skompilowane zapytanie XPath zwrócone z metody static <xref:System.Xml.XPath.XPathExpression.Compile%2A> klasy <xref:System.Xml.XPath.XPathExpression> lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="the-xpathexpression-class"></a>Klasa XPathExpression  
 Skompilowane zapytanie XPath reprezentowane przez obiekt <xref:System.Xml.XPath.XPathExpression> jest przydatne, jeśli ta sama kwerenda XPath jest używana więcej niż raz.  
  
 Na przykład w przypadku wywołania metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> wiele razy zamiast używania ciągu reprezentującego kwerendę XPath za każdym razem użyj metody <xref:System.Xml.XPath.XPathExpression.Compile%2A> klasy <xref:System.Xml.XPath.XPathExpression> lub metody <xref:System.Xml.XPath.XPathNavigator.Compile%2A> klasy <xref:System.Xml.XPath.XPathNavigator> do kompilowania i buforowania zapytania XPath w obiekcie <xref:System.Xml.XPath.XPathExpression>, aby ponownie wykorzystać i zwiększyć wydajność.  
  
 Po skompilowaniu obiekt <xref:System.Xml.XPath.XPathExpression> może być używany jako dane wejściowe do poniższych metod klasy <xref:System.Xml.XPath.XPathNavigator> w zależności od typu zwracanego z kwerendy XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 W poniższej tabeli opisano wszystkie typy zwracane w formacie W3C XPath, ich Microsoft .NET Framework equivalencies i metody, z których może korzystać obiekt <xref:System.Xml.XPath.XPathExpression>, w zależności od typu zwracanego.  
  
|Typ zwracany XPath W3C|Typ odpowiedni .NET Framework|Opis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Nieuporządkowana kolekcja węzłów bez duplikatów utworzonych w kolejności dokumentu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Wartość `true` lub `false`.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Liczba zmiennoprzecinkowa.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Sekwencja znaków UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> akceptuje wyrażenie XPath jako parametr. Metoda <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> zwraca obiekt <xref:System.Xml.XPath.XPathNavigator>, a nie jeden z typów zwracanych w formacie xmlxpath.  
  
### <a name="the-returntype-property"></a>Właściwość ReturnType  
 Po skompilowaniu zapytania XPath do obiektu <xref:System.Xml.XPath.XPathExpression> można użyć właściwości <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> obiektu <xref:System.Xml.XPath.XPathExpression>, aby określić, co zwraca zapytanie XPath.  
  
 Właściwość <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> wartości wyliczenia reprezentujących typy zwracane w formacie W3C XPath.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Poniższy przykład używa obiektu <xref:System.Xml.XPath.XPathExpression>, aby zwrócić numer i zestaw węzłów z pliku `books.xml`. Właściwość <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> każdego obiektu <xref:System.Xml.XPath.XPathExpression>, a także wyniki <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane w konsoli programu.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 Przykład pobiera `books.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Wyrażenia XPath o wyższej wydajności  
 Aby uzyskać lepszą wydajność, użyj najbardziej określonego wyrażenia XPath możliwego w zapytaniach. Na przykład, jeśli węzeł `book` jest węzłem podrzędnym węzła `bookstore`, a węzeł `bookstore` jest elementem najwyższego poziomu w dokumencie XML, użycie wyrażenia XPath `/bookstore/book` jest szybsze niż użycie `//book`. `//book` wyrażenie XPath skanuje każdy węzeł w drzewie XML, aby zidentyfikować pasujące węzły.  
  
 Ponadto przy użyciu metod nawigacji zestawu węzłów dostarczonych przez klasę <xref:System.Xml.XPath.XPathNavigator> może spowodować zwiększenie wydajności na podstawie metod wyboru dostarczonych przez klasę <xref:System.Xml.XPath.XPathNavigator> w przypadkach, gdy kryteria wyboru są proste. Na przykład, jeśli trzeba wybrać pierwszy element podrzędny bieżącego węzła, można użyć metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>ej, aby użyć `child::*[1]` wyrażenia XPath i metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.  
  
 Aby uzyskać więcej informacji na temat metod nawigacji zestawu węzłów klasy <xref:System.Xml.XPath.XPathNavigator>, zobacz [Nawigacja zestawu węzłów za pomocą elementu XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
