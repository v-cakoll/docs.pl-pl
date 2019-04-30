---
title: Skompilowane wyrażenia XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1716488f6e072b09469dfbe5cc8fb4965e5db44c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669137"
---
# <a name="compiled-xpath-expressions"></a>Skompilowane wyrażenia XPath
<xref:System.Xml.XPath.XPathExpression> Obiekt reprezentuje kompilowanym zapytaniu XPath zwróciło albo statycznych <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
## <a name="the-xpathexpression-class"></a>Klasa XPathExpression  
 A skompilowany zapytanie XPath, reprezentowane przez <xref:System.Xml.XPath.XPathExpression> obiekt jest przydatne, jeśli to samo zapytanie XPath jest używana w więcej niż jeden raz.  
  
 Na przykład podczas wywoływania <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda wielokrotnie, zamiast korzystać z ciągu reprezentującego Kwerenda XPath każdorazowo, użyj <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy do kompilowania i Zapytanie XPath w pamięci podręcznej <xref:System.Xml.XPath.XPathExpression> obiekt do ponownego użycia i wydajności.  
  
 Po skompilowaniu <xref:System.Xml.XPath.XPathExpression> obiekt może być używany jako dane wejściowe dla następujących <xref:System.Xml.XPath.XPathNavigator> metody klasy, w zależności od typu zwróconych przez kwerendę XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 W poniższej tabeli opisano każdy z typów zwracanych W3C XPath, ich equivalencies programu Microsoft .NET Framework i co metody <xref:System.Xml.XPath.XPathExpression> obiektu może być używany z na podstawie jego typu zwracanego.  
  
|Typ zwracany XPath W3C|Typ równoważne programu .NET framework|Opis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Nieuporządkowanej kolekcji węzłów bez duplikatów tworzone w kolejności dokumentu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` lub `false` wartość.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Liczba zmiennoprzecinkowa.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Sekwencja znaków UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda przyjmuje jako parametr wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda zwraca <xref:System.Xml.XPath.XPathNavigator> obiektu, nie jeden z typów zwracanych W3C XPath.  
  
### <a name="the-returntype-property"></a>Właściwość ReturnType  
 Po XPath skompilowaniu zapytania do <xref:System.Xml.XPath.XPathExpression> obiektu, możesz użyć <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> właściwość <xref:System.Xml.XPath.XPathExpression> obiektu, aby określić zapytanie XPath zwraca.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwość zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> typów zwracanych wartości wyliczenia reprezentujący W3C XPath.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathExpression> obiekt do zwrotu numeru i węzeł z `books.xml` pliku. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwości każdego <xref:System.Xml.XPath.XPathExpression> obiektu oraz wyniki z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane do konsoli.  
  
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
  
 Przykład przyjmuje `books.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Wyrażenia XPath w usłudze wyższej wydajności  
 Lepszą wydajność należy użyć bardziej konkretny od pozostałych wyrażenia XPath w zapytaniach. Na przykład jeśli `book` węzeł jest elementem podrzędnym `bookstore` węzła i `bookstore` węzeł jest elementem najważniejsze w dokumencie XML za pomocą wyrażenia XPath `/bookstore/book` jest szybsza niż przy użyciu `//book`. `//book` Wyrażenie XPath przeskanuje każdego węzła w drzewie XML, aby zidentyfikować pasujące węzły.  
  
 Ponadto, korzystając z węzła ustawić nawigacji metod dostarczonych przez <xref:System.Xml.XPath.XPathNavigator> klasy może spowodować lepszą wydajność za pośrednictwem metody dostarczone przez <xref:System.Xml.XPath.XPathNavigator> klasy w przypadkach, gdy kryteria wyboru są proste. Na przykład, chcąc pierwszego elementu podrzędnego bieżącego węzła jest szybsze użyj <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metoda niż korzystać `child::*[1]` wyrażenie XPath i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.  
  
 Aby uzyskać więcej informacji na temat węzła zestawu metod nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy, zobacz [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
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
