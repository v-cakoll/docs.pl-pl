---
title: Skompilowane wyrażenia XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: e74b52e471699fc663504fa42d6c7e502859adda
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291529"
---
# <a name="compiled-xpath-expressions"></a>Skompilowane wyrażenia XPath
<xref:System.Xml.XPath.XPathExpression>Obiekt reprezentuje skompilowane zapytanie XPath zwrócone z metody statycznej <xref:System.Xml.XPath.XPathExpression.Compile%2A> <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
## <a name="the-xpathexpression-class"></a>Klasa XPathExpression  
 Skompilowane zapytanie XPath reprezentowane przez <xref:System.Xml.XPath.XPathExpression> obiekt jest przydatne, jeśli ta sama kwerenda XPath jest używana więcej niż raz.  
  
 Na przykład podczas wywoływania <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody wielokrotnie, zamiast używać ciągu reprezentującego kwerendę XPath za każdym razem, użyj <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy do kompilowania i buforowania zapytania XPath w <xref:System.Xml.XPath.XPathExpression> obiekcie w celu ponownego użycia i zwiększenia wydajności.  
  
 Po skompilowaniu <xref:System.Xml.XPath.XPathExpression> obiekt może być używany jako dane wejściowe dla następujących <xref:System.Xml.XPath.XPathNavigator> metod klasy w zależności od typu zwracanego z kwerendy XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 W poniższej tabeli opisano każdy z typów zwracanych przez konsorcjum W3C XPath, ich Microsoft .NET Framework equivalencies i metody, <xref:System.Xml.XPath.XPathExpression> z których może korzystać obiekt na podstawie zwracanego typu.  
  
|Typ zwracany XPath W3C|Typ odpowiedni .NET Framework|Opis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Nieuporządkowana kolekcja węzłów bez duplikatów utworzonych w kolejności dokumentu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Wartość `true` lub `false`.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Liczba zmiennoprzecinkowa.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Sekwencja znaków UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Metoda akceptuje wyrażenie XPath jako parametr. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>Metoda zwraca <xref:System.Xml.XPath.XPathNavigator> obiekt, a nie jeden z typów zwracanych w formacie XPath.  
  
### <a name="the-returntype-property"></a>Właściwość ReturnType  
 Po skompilowaniu zapytania XPath do <xref:System.Xml.XPath.XPathExpression> obiektu można użyć <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> właściwości <xref:System.Xml.XPath.XPathExpression> obiektu, aby określić, co zwraca zapytanie XPath.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>Właściwość zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> wartości wyliczenia reprezentujących typy zwracane W3C XPath.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Poniższy przykład używa <xref:System.Xml.XPath.XPathExpression> obiektu do zwrócenia numeru i zestawu węzłów z `books.xml` pliku. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>Właściwość każdego <xref:System.Xml.XPath.XPathExpression> obiektu, a także wyniki z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane w konsoli programu.  
  
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
 Aby uzyskać lepszą wydajność, użyj najbardziej określonego wyrażenia XPath możliwego w zapytaniach. Na przykład, jeśli `book` węzeł jest węzłem podrzędnym węzła, `bookstore` a `bookstore` węzeł jest elementem najwyższego poziomu w dokumencie XML, użycie wyrażenia XPath `/bookstore/book` jest szybsze niż używanie `//book` . `//book`Wyrażenie XPath skanuje każdy węzeł w drzewie XML, aby zidentyfikować pasujące węzły.  
  
 Ponadto przy użyciu metody nawigacji zestawu węzłów dostarczonej przez <xref:System.Xml.XPath.XPathNavigator> klasę mogą spowodować zwiększenie wydajności na podstawie metod wyboru dostarczonych przez <xref:System.Xml.XPath.XPathNavigator> klasę w przypadkach, gdy kryteria wyboru są proste. Na przykład, jeśli trzeba wybrać pierwszy element podrzędny bieżącego węzła, można użyć <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metody, aby użyć `child::*[1]` wyrażenia XPath i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.  
  
 Aby uzyskać więcej informacji o metodach nawigacji zestawu węzłów <xref:System.Xml.XPath.XPathNavigator> klasy, zobacz [nawigowanie po węźle przy użyciu elementu XPathNavigator](node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](node-types-recognized-with-xpath-queries.md)
- [Zapytania XPath i przestrzenie nazw](xpath-queries-and-namespaces.md)
