---
title: Usuwanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710365"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Usuwanie danych XML przy użyciu klasy XPathNavigator
Klasa <xref:System.Xml.XPath.XPathNavigator> zawiera zestaw metod służących do usuwania węzłów i wartości z dokumentu XML. Aby można było korzystać z tych metod, obiekt <xref:System.Xml.XPath.XPathNavigator> musi być edytowalny, oznacza to, że jego właściwość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiektów, które mogą edytować dokument XML, są tworzone przez metodę <xref:System.Xml.XmlDocument.CreateNavigator%2A> klasy <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> obiektów utworzonych przez klasę <xref:System.Xml.XPath.XPathDocument> są tylko do odczytu, a każda próba użycia metod edycji obiektu <xref:System.Xml.XPath.XPathNavigator> utworzonego przez obiekt <xref:System.Xml.XPath.XPathDocument> powoduje <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji na temat tworzenia edytowalnych obiektów <xref:System.Xml.XPath.XPathNavigator>, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Usuwanie węzłów  
 Klasa <xref:System.Xml.XPath.XPathNavigator> zapewnia metodę <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> do usuwania węzłów z dokumentu XML.  
  
### <a name="removing-a-node"></a>Usuwanie węzła  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia metodę <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>, aby usunąć bieżący węzeł, w którym obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony w dokumencie XML.  
  
 Po usunięciu węzła przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> nie jest on już dostępny z poziomu korzenia obiektu <xref:System.Xml.XmlDocument>. Po usunięciu węzła <xref:System.Xml.XPath.XPathNavigator> zostanie umieszczony w węźle nadrzędnym usuniętego węzła.  
  
 Operacja usuwania nie ma wpływu na pozycję żadnego obiektu <xref:System.Xml.XPath.XPathNavigator> umieszczonym w usuniętym węźle. Te <xref:System.Xml.XPath.XPathNavigator> obiekty są prawidłowe w tym sensie, że mogą one poruszać się w usuniętym poddrzewie, ale nie można ich przenieść do głównego drzewa węzłów przy użyciu metod nawigacji zestawu węzłów klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> Metoda <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> klasy <xref:System.Xml.XPath.XPathNavigator> może służyć do przenoszenia tych <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do głównego drzewa węzłów lub z drzewa głównego węzła do usuniętego poddrzewa.  
  
 W poniższym przykładzie element `price` pierwszego elementu `book` pliku `contosoBooks.xml` jest usuwany przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>. Pozycja obiektu <xref:System.Xml.XPath.XPathNavigator> po usunięciu elementu `price` znajduje się w elemencie nadrzędnym `book`.  
  
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
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Usuwanie węzła atrybutu  
 Węzły atrybutów są usuwane z dokumentu XML przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.  
  
 Po usunięciu węzła atrybutu nie jest on już osiągalny z węzła głównego obiektu <xref:System.Xml.XmlDocument>, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest umieszczony na elemencie nadrzędnym.  
  
#### <a name="default-attributes"></a>Atrybuty domyślne  
 Niezależnie od metody używanej do usuwania atrybutów istnieją specjalne ograniczenia dotyczące usuwania atrybutów, które są zdefiniowane jako atrybuty domyślne w schemacie DTD lub XML dla dokumentu XML. Atrybutów domyślnych nie można usunąć, chyba że element, do którego należą, został również usunięty. Atrybuty domyślne są zawsze obecne dla elementów, które mają zadeklarowane atrybuty domyślne i w związku z tym usunięcie atrybutu domyślnego powoduje wstawianie atrybutu zastępczego do elementu i zainicjowanie do wartości domyślnej, która została zadeklarowana.  
  
## <a name="removing-values"></a>Usuwanie wartości  
 Klasa <xref:System.Xml.XPath.XPathNavigator> dostarcza metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, aby usunąć wartości niewpisane i wpisane z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Usuwanie niewpisanych wartości  
 Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> po prostu wstawia wartość nietypu `string` przekazaną jako parametr jako wartość węzła, w którym obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony. Przekazanie pustego ciągu do metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> powoduje usunięcie wartości bieżącego węzła.  
  
 Poniższy przykład usuwa wartość elementu `price` pierwszego elementu `book` w pliku `contosoBooks.xml` przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>.  
  
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
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Usuwanie wpisanych wartości  
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez metodę <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` dla elementu, którego typem jest `xs:positiveInteger`), powoduje wyjątek. Metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> nie można również przekazywać `null` jako parametru. W wyniku usunięcia wartości węzła o określonym typie musi być zgodna z typem schematu węzła.  
  
 Poniższy przykład usuwa wartość elementu `price` pierwszego elementu `book` w pliku `contosoBooks.xml` przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przez ustawienie wartości na `0`. Wartość węzła nie jest usuwana, ale cena księgi została usunięta zgodnie z jej typem danych `xs:decimal`.  
  
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
  
## <a name="namespace-nodes"></a>Węzły przestrzeni nazw  
 Nie można usunąć węzłów przestrzeni nazw z obiektu <xref:System.Xml.XmlDocument>. Próba usunięcia węzłów przestrzeni nazw przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> powoduje wyjątek.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości InnerXml i OuterXml  
 Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy <xref:System.Xml.XPath.XPathNavigator> zmieniają znaczniki XML dla węzłów, w których jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
 Właściwość <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony w przeanalizowanej zawartości danego `string`XML. Podobnie Właściwość <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony, a także bieżący węzeł.  
  
 Poza metodami opisanymi w tym temacie właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą służyć do usuwania węzłów i wartości z dokumentu XML. Aby uzyskać więcej informacji na temat używania właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> do modyfikowania węzłów, zobacz temat [modyfikowanie danych XML przy użyciu elementu XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument> w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod klasy <xref:System.Xml.XmlDocument>. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument>, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
