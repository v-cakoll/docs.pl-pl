---
title: Zapytania XPath i przestrzenie nazw
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: 91503ce0bffa1a9390432a51bff1ef10d80f563a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709780"
---
# <a name="xpath-queries-and-namespaces"></a>Zapytania XPath i przestrzenie nazw
Zapytania XPath są świadome przestrzeni nazw w dokumencie XML i mogą używać prefiksów przestrzeni nazw do kwalifikowania nazw elementów i atrybutów. Kwalifikujące się nazwy elementów i atrybutów z prefiksem przestrzeni nazw ograniczają węzły zwracane przez zapytanie XPath tylko do tych węzłów, które należą do określonej przestrzeni nazw.  
  
 Na przykład jeśli `books` prefiks mapuje do przestrzeni nazw `http://www.contoso.com/books`, następujące zapytanie `/books:books/books:book` XPath wybiera tylko te `book` elementy w przestrzeni nazw. `http://www.contoso.com/books`  
  
## <a name="the-xmlnamespacemanager"></a>Nazwa XmlNamespaceManager  
 Aby używać przestrzeni nazw w zapytaniu XPath, obiekt pochodzący z <xref:System.Xml.IXmlNamespaceResolver> interfejsu, takiego <xref:System.Xml.XmlNamespaceManager> jak Klasa, jest konstruowany przy użyciu identyfikatora URI przestrzeni nazw i prefiksu do uwzględnienia w zapytaniu XPath.  
  
 <xref:System.Xml.XmlNamespaceManager> Obiekt może być używany w zapytaniu w każdym z poniższych sposobów.  
  
- <xref:System.Xml.XmlNamespaceManager> Obiekt jest skojarzony z istniejącym <xref:System.Xml.XPath.XPathExpression> obiektem za pomocą <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metody <xref:System.Xml.XPath.XPathExpression> obiektu. Możesz również <xref:System.Xml.XPath.XPathExpression> skompilować nowy obiekt za pomocą metody statycznej <xref:System.Xml.XPath.XPathExpression.Compile%2A> , która przyjmuje ciąg reprezentujący wyrażenie XPath i <xref:System.Xml.XmlNamespaceManager> obiekt jako parametry i zwraca nowy <xref:System.Xml.XPath.XPathExpression> obiekt.  
  
- Sam <xref:System.Xml.XmlNamespaceManager> obiekt jest przekazaniem jako parametr do metody akceptującej <xref:System.Xml.XPath.XPathNavigator> klasy wraz z ciągiem reprezentującym wyrażenie XPath.  
  
 Poniżej przedstawiono metody <xref:System.Xml.XPath.XPathNavigator> klasy, które akceptują obiekt pochodny <xref:System.Xml.IXmlNamespaceResolver> interfejsu jako parametr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Domyślna przestrzeń nazw  
 W poniższym dokumencie XML, domyślna przestrzeń nazw z pustym prefiksem jest używana do deklarowania `http://www.contoso.com/books` przestrzeni nazw.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 Wyrażenie XPath traktuje pusty prefiks jako `null` przestrzeń nazw. Innymi słowy, tylko prefiksy mapowane na przestrzenie nazw mogą być używane w zapytaniach XPath. Oznacza to, że jeśli chcesz wykonać zapytanie względem przestrzeni nazw w dokumencie XML, nawet jeśli jest to domyślna przestrzeń nazw, musisz zdefiniować dla niej prefiks.  
  
 Na przykład bez definiowania prefiksu dla dokumentu XML powyżej zapytanie `/books/book` XPath nie zwróci żadnych wyników.  
  
 Prefiks musi być powiązany, aby zapobiec niejednoznaczności podczas wykonywania zapytania o dokumenty z niektórymi węzłami, a niektóre w domyślnej przestrzeni nazw.  
  
 Poniższy kod definiuje prefiks domyślnej przestrzeni nazw i wybiera wszystkie `book` elementy z `http://www.contoso.com/books` przestrzeni nazw.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wybieranie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Dopasowywanie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Typy węzłów rozpoznawanych w zapytaniach XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Skompilowane wyrażenia XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
