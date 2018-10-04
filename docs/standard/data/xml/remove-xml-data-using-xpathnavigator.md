---
title: Usuwanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781560"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Usuwanie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które służy do usuwania węzłów i wartości z dokumentu XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być niemożliwa, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są przeznaczone tylko do odczytu i dowolne próba należy użyć metod edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> skutkuje obiektu <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu edytowalne <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Usuwanie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodę, aby usunąć węzły z dokumentu XML.  
  
### <a name="removing-a-node"></a>Usuwanie węzła  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodę, aby usunąć bieżący węzeł <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na z dokumentu XML.  
  
 Po usunięciu węzła przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, nie jest już dostępny z poziomu katalogu głównego <xref:System.Xml.XmlDocument> obiektu. Po usunięciu węzła <xref:System.Xml.XPath.XPathNavigator> znajduje się w węźle nadrzędnym usuniętego węzła.  
  
 Operacja usunięcia nie ma wpływu na pozycję żadnego <xref:System.Xml.XPath.XPathNavigator> obiektu umieszczony na usuniętego węzła. Te <xref:System.Xml.XPath.XPathNavigator> obiekty są prawidłowe w tym sensie, że można przenieść w poddrzewie usunięte, ale nie może być przeniesiona węzeł główny drzewa za pomocą regularnego węzeł zestaw metod nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metody <xref:System.Xml.XPath.XPathNavigator> klasy można je przenieść <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do głównego węzła drzewa lub z węzła głównego drzewa do usuniętego poddrzewo.  
  
 W poniższym przykładzie `price` element pierwszego `book` elementu `contosoBooks.xml` plik zostanie usunięty przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody. Pozycja <xref:System.Xml.XPath.XPathNavigator> obiektu po `price` element został usunięty znajduje się na element nadrzędny `book` elementu.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Usuwanie węzła atrybutu  
 Węzłów atrybutu są usuwane z dokumentu XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.  
  
 Po usunięciu węzła atrybutu nie jest już dostępny z głównego węzła <xref:System.Xml.XmlDocument> obiektu i <xref:System.Xml.XPath.XPathNavigator> obiekt zostanie umieszczony w elemencie nadrzędnym.  
  
#### <a name="default-attributes"></a>Atrybuty domyślne  
 Niezależnie od metody, aby usunąć atrybuty istnieją specjalne ograniczenia na temat usuwania atrybutów, które są zdefiniowane jako atrybuty domyślnych w DTD lub schematu XML w dokumencie XML. Nie można usunąć domyślnych atrybutów, chyba że element, do którego należą one do zostaną również usunięte. Atrybuty domyślne są zawsze obecne elementy, które mają domyślnych atrybutów zadeklarowany, co w efekcie usuwanie wyników atrybut domyślny atrybut zastępczy jest wstawiany do elementu i zainicjowany do wartości domyślnej, który został zadeklarowany.  
  
## <a name="removing-values"></a>Usuwanie wartości  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, aby usunąć bez typu i wpisane wartości z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Usuwanie wartości bez typu  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia nietypizowane `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na. Przekazywanie pusty ciąg, aby <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda usuwa wartość bieżącego węzła.  
  
 Poniższy przykład usuwa wartość `price` element pierwszego `book` element `contosoBooks.xml` plików przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Usuwanie wartości Typizowane  
 Gdy typ węzła jest schematu XML W3C prosty typ, nowej wartości, które są wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody jest sprawdzana względem aspekty typu prostego, zanim ma wartość. Jeśli nowa wartość nie jest nieprawidłowa według typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wyjątek. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Również nie mogą być przekazywane metoda `null` jako parametr. W wyniku usuwania wartość węzła typu muszą być zgodne z typem schematu węzła.  
  
 Poniższy przykład usuwa wartość `price` element pierwszego `book` element `contosoBooks.xml` plików przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody przez ustawienie wartości `0`. Wartość węzła nie jest usuwany, ale ceny książki został usunięty zgodnie z jego typu danych `xs:decimal`.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>Węzły Namespace  
 Nie można usunąć węzłów Namespace z <xref:System.Xml.XmlDocument> obiektu. Próbuje usunąć węzły przestrzeni nazw za pomocą <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda nie powoduje wyjątek.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości OuterXml i elementu  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zmienić węzłów znaczniki XML <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> przeanalizowany zawartość XML danego obiektu aktualnie jest ustawiony na `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiektu aktualnie jest ustawiony na oraz bieżącego węzła.  
  
 Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości służy do usuwania węzłów i wartości z dokumentu XML. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości modyfikujące węzłów, zobacz [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiektu jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian <xref:System.Xml.XmlDocument> obiektu, zobacz [zapisywania i zapisywania dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
