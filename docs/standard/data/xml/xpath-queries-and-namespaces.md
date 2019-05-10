---
title: Zapytania XPath i przestrzenie nazw
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0704e78a0e7fbf3987b3bc75bb46e135f00110e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615349"
---
# <a name="xpath-queries-and-namespaces"></a>Zapytania XPath i przestrzenie nazw
Zapytania XPath zdawali sobie sprawę z przestrzeni nazw w dokumencie XML i użyć prefiksy przestrzeni nazw do kwalifikowania nazwy elementów i atrybutów. Kwalifikowanie nazw elementów i atrybutów z prefiksem nazw ogranicza węzłów zwróconych przez zapytanie XPath do tych węzłów, które należą do określonego obszaru nazw.  
  
 Na przykład jeśli prefiks `books` mapuje do przestrzeni nazw `http://www.contoso.com/books`, następnie następujące zapytanie XPath `/books:books/books:book` wybiera tylko te `book` elementów w przestrzeni nazw `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Aby użyć przestrzeni nazw w zapytaniu XPath, obiekt pochodzi od <xref:System.Xml.IXmlNamespaceResolver> interfejsu, takich jak <xref:System.Xml.XmlNamespaceManager> klasy jest konstruowany przy użyciu identyfikatora URI obszaru nazw i prefiks do uwzględnienia w zapytaniu XPath.  
  
 <xref:System.Xml.XmlNamespaceManager> Obiekt może być używany w zapytania w każdym z następujących sposobów.  
  
- <xref:System.Xml.XmlNamespaceManager> Obiekt jest skojarzony z istniejącym <xref:System.Xml.XPath.XPathExpression> obiektu za pomocą <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metody <xref:System.Xml.XPath.XPathExpression> obiektu. Również skompilować nowego <xref:System.Xml.XPath.XPathExpression> przy użyciu statycznych <xref:System.Xml.XPath.XPathExpression.Compile%2A> metoda przyjmująca ciąg reprezentujący wyrażenie XPath i <xref:System.Xml.XmlNamespaceManager> obiektu jako parametrów i zwraca nowy <xref:System.Xml.XPath.XPathExpression> obiektu.  
  
- <xref:System.Xml.XmlNamespaceManager> Sam obiekt jest przekazywany jako parametr do akceptowania <xref:System.Xml.XPath.XPathNavigator> metody wraz z ciągiem reprezentującym wyrażenie XPath klasy.  
  
 Poniżej przedstawiono metody <xref:System.Xml.XPath.XPathNavigator> pochodną klasę, która akceptuje obiekt <xref:System.Xml.IXmlNamespaceResolver> interfejsu jako parametr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Namespace domyślne  
 W dokumencie XML, który następuje po, domyślny obszar nazw, przy użyciu pustego prefiksu jest używane do deklarowania `http://www.contoso.com/books` przestrzeni nazw.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 Wyrażenie XPath traktuje pustego prefiksu jako `null` przestrzeni nazw. Innymi słowy tylko prefiksy mapowane do przestrzeni nazw może służyć w zapytaniach XPath. Oznacza to, jeśli chcesz się do wykonywania zapytań w przestrzeni nazw w dokumencie XML, nawet jeśli jest ona domyślny obszar nazw, należy określić prefiks dla niego.  
  
 Na przykład, bez zdefiniowania prefiksu dla dokumentu XML powyżej wyrażenie XPath kwerenda `/books/book` nie zwróci żadnych wyników.  
  
 Prefiks, który musi być powiązana, aby uniknąć niejednoznaczności, podczas wykonywania zapytań dotyczących dokumentów za pomocą niektóre węzły nie w przestrzeni nazw, a niektóre w domyślnej przestrzeni nazw.  
  
 Poniższy kod definiuje prefiks dla domyślny obszar nazw i zaznacza wszystkie `book` elementy z `http://www.contoso.com/books` przestrzeni nazw.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
