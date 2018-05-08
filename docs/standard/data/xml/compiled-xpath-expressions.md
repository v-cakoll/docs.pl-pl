---
title: Wyrażenia XPath skompilowanych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bee210b12c588163a3e11dfdab4dadda9ec0c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiled-xpath-expressions"></a>Wyrażenia XPath skompilowanych
<xref:System.Xml.XPath.XPathExpression> Obiekt reprezentuje skompilowanym zapytaniu XPath zwrócony z albo statycznych <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
## <a name="the-xpathexpression-class"></a>Klasa XPathExpression  
 A skompilowane zapytanie XPath reprezentowany przez <xref:System.Xml.XPath.XPathExpression> obiekt jest przydatne, jeśli to samo zapytanie XPath jest używana więcej niż raz.  
  
 Na przykład podczas wywoływania metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> — metoda wielokrotnie, zamiast ciąg reprezentujący zapytanie XPath zawsze używać <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy do kompilowania i Buforuj zapytanie XPath w <xref:System.Xml.XPath.XPathExpression> obiekt do ponownego użycia i wydajności.  
  
 Raz skompilowany, <xref:System.Xml.XPath.XPathExpression> obiekt może służyć jako dane wejściowe dla następujących <xref:System.Xml.XPath.XPathNavigator> metody klasy, w zależności od typu zwróconych przez kwerendę XPath.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 W poniższej tabeli opisano typy zwracane W3C XPath, ich equivalencies programu Microsoft .NET Framework i co metody <xref:System.Xml.XPath.XPathExpression> obiektu może być używana z oparte na jej typu zwracanego.  
  
|Typ zwracany XPath W3C|.NET framework odpowiednik typu|Opis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Kolekcja nieuporządkowana węzłów bez duplikaty są tworzone w kolejności dokumentu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` lub `false` wartość.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Liczba zmiennoprzecinkowa.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Sekwencja znaków UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda przyjmuje jako jego parametr wyrażenia XPath. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda zwraca <xref:System.Xml.XPath.XPathNavigator> obiekt nie jest elementem W3C XPath zwracanych typów.  
  
### <a name="the-returntype-property"></a>Właściwość ReturnType  
 Po XPath skompilowaniu zapytania do <xref:System.Xml.XPath.XPathExpression> obiektu, można użyć <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> właściwość <xref:System.Xml.XPath.XPathExpression> obiektem, aby określić zwraca zapytanie XPath.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwość zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> typy zwracane wartości wyliczenia reprezentujący W3C XPath.  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathExpression> obiektu do zwrócenia numer i ustaw z węzła `books.xml` pliku. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwości każdego <xref:System.Xml.XPath.XPathExpression> obiektów oraz wyniki z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane do konsoli.  
  
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
  
### <a name="higher-performance-xpath-expressions"></a>Wyższa wydajność XPath wyrażenia  
 W celu poprawy wydajności użyj specyficzny możliwe zapytania wyrażenie XPath. Na przykład jeśli `book` węzeł jest elementem podrzędnym `bookstore` węzła i `bookstore` węzeł jest elementem najwyższy w dokumencie XML za pomocą wyrażenia XPath `/bookstore/book` jest szybsza niż przy użyciu `//book`. `//book` Wyrażenie XPath skanuje każdy węzeł w drzewie XML, aby zidentyfikować zgodne węzły.  
  
 Ponadto, za pomocą węzła ustawić metod nawigacji dostarczonych przez <xref:System.Xml.XPath.XPathNavigator> klasy może spowodować lepszą wydajność za pośrednictwem metody wyboru dostarczonych przez <xref:System.Xml.XPath.XPathNavigator> klasy w przypadkach, gdy kryteria wyboru są proste. Na przykład, jeśli musisz wybrać pierwszym elementem podrzędnym bieżącego węzła, jest szybsze do użycia <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metody niż korzystać `child::*[1]` wyrażenie XPath i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.  
  
 Aby uzyskać więcej informacji na temat węzeł Ustaw metody nawigacji <xref:System.Xml.XPath.XPathNavigator> , zobacz [węzła ustawić nawigacji przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Zapytania XPath i przestrzenie nazw](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
