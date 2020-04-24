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
<xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod służących do usuwania węzłów i wartości z dokumentu XML. Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> że jego właściwość `true`musi być.  
  
 <xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy <xref:System.Xml.XmlDocument.CreateNavigator%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator>obiekty utworzone <xref:System.Xml.XPath.XPathDocument> przez klasę są tylko do odczytu, a każda próba użycia metod <xref:System.Xml.XPath.XPathNavigator> edycji obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt daje w wyniku. <xref:System.NotSupportedException>  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator> tworzenia edytowalnych obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Usuwanie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodę usuwania węzłów z dokumentu XML.  
  
### <a name="removing-a-node"></a>Usuwanie węzła  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodę usuwania bieżącego węzła, <xref:System.Xml.XPath.XPathNavigator> który obiekt jest obecnie umieszczony na podstawie dokumentu XML.  
  
 Po usunięciu węzła przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody nie jest on już dostępny z poziomu korzenia <xref:System.Xml.XmlDocument> obiektu. Po usunięciu węzła <xref:System.Xml.XPath.XPathNavigator> jest on umieszczany w węźle nadrzędnym usuniętego węzła.  
  
 Operacja usuwania nie wpływa na położenie żadnego <xref:System.Xml.XPath.XPathNavigator> obiektu umieszczonego w usuniętym węźle. Te <xref:System.Xml.XPath.XPathNavigator> obiekty są prawidłowe w tym sensie, że mogą one poruszać się w usuniętych poddrzewach, ale nie można ich przenieść do głównego drzewa węzłów przy użyciu standardowych metod <xref:System.Xml.XPath.XPathNavigator> nawigacji zestawu węzłów klasy.  
  
> [!NOTE]
> Metoda klasy może służyć do przenoszenia tych <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do głównego drzewa węzłów lub z drzewa głównego węzła do usuniętego poddrzewa. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
 `price` W poniższym przykładzie element `book` pierwszego elementu `contosoBooks.xml` pliku jest usuwany przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody. Pozycja <xref:System.Xml.XPath.XPathNavigator> obiektu po usunięciu `price` elementu znajduje się w elemencie nadrzędnym. `book`  
  
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
 Węzły atrybutów są usuwane z dokumentu XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.  
  
 Po usunięciu węzła atrybutu nie jest on już osiągalny z węzła głównego <xref:System.Xml.XmlDocument> obiektu, a <xref:System.Xml.XPath.XPathNavigator> obiekt jest umieszczony w elemencie nadrzędnym.  
  
#### <a name="default-attributes"></a>Atrybuty domyślne  
 Niezależnie od metody używanej do usuwania atrybutów istnieją specjalne ograniczenia dotyczące usuwania atrybutów, które są zdefiniowane jako atrybuty domyślne w schemacie DTD lub XML dla dokumentu XML. Atrybutów domyślnych nie można usunąć, chyba że element, do którego należą, został również usunięty. Atrybuty domyślne są zawsze obecne dla elementów, które mają zadeklarowane atrybuty domyślne i w związku z tym usunięcie atrybutu domyślnego powoduje wstawianie atrybutu zastępczego do elementu i zainicjowanie do wartości domyślnej, która została zadeklarowana.  
  
## <a name="removing-values"></a>Usuwanie wartości  
 <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> do usuwania wartości typu untyped i Type z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Usuwanie niewpisanych wartości  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia `string` wartość bez typu jako parametr jako wartość węzła, na którym <xref:System.Xml.XPath.XPathNavigator> znajduje się obiekt. Przekazanie pustego ciągu do <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody powoduje usunięcie wartości bieżącego węzła.  
  
 Poniższy przykład `price` usuwa wartość elementu pierwszego `book` elementu w `contosoBooks.xml` pliku przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.  
  
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
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger`), powoduje wyjątek. Nie <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> można również przekazywać `null` metody jako parametru. W wyniku usunięcia wartości węzła o określonym typie musi być zgodna z typem schematu węzła.  
  
 Poniższy `price` przykład usuwa wartość elementu pierwszego `book` elementu w `contosoBooks.xml` pliku przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody przez ustawienie wartości. `0` Wartość węzła nie jest usuwana, ale cena księgi została usunięta przy uwzględnieniu jej typu danych `xs:decimal`.  
  
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
 Nie można usunąć węzłów przestrzeni nazw z <xref:System.Xml.XmlDocument> obiektu. Próba usunięcia węzłów przestrzeni nazw przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody powoduje wyjątek.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości InnerXml i OuterXml  
 Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> <xref:System.Xml.XPath.XPathNavigator> klasy zmieniają znaczniki XML w węzłach, w których <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwość zmienia znaczniki XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML węzłów podrzędnych, w których <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony, a także bieżący węzeł.  
  
 Poza metodami opisanymi w tym temacie, właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą być używane do usuwania węzłów i wartości z dokumentu XML. Aby uzyskać więcej informacji o <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> korzystaniu <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> z właściwości i do modyfikowania węzłów, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
