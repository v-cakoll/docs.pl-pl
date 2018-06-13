---
title: Usuwanie danych XML przy użyciu parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dc7d83692f081f2c48a34cef8a33564f0e3089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577036"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Usuwanie danych XML przy użyciu parametrem XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod służy do usuwania węzłów i wartości z dokumentu XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są tylko do odczytu i próby użycia metody edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> obiektu powoduje <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu można edytować <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Usuwanie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody do usuwania węzłów z dokumentu XML.  
  
### <a name="removing-a-node"></a>Usunięcie węzła  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> do usunięcia z bieżącego węzła <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na z dokumentu XML.  
  
 Po usunięciu węzła przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, nie jest już dostępny od elementu głównego <xref:System.Xml.XmlDocument> obiektu. Po usunięciu węzła <xref:System.Xml.XPath.XPathNavigator> znajduje się w węźle nadrzędnym usuniętego węzła.  
  
 Operacja usuwania nie ma wpływu na pozycję żadnego <xref:System.Xml.XPath.XPathNavigator> znajduje się w węźle usuniętego obiektu. Te <xref:System.Xml.XPath.XPathNavigator> obiektów są dozwolone w tym sensie, że można przenosić między usunięto poddrzewo, ale nie można przenieść węzła głównego drzewa przy użyciu węzła regularne Ustaw metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metody <xref:System.Xml.XPath.XPathNavigator> klasa umożliwia przeniesienie tych <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do węzła głównego drzewa lub z węzła głównego drzewa do usuniętego poddrzewo.  
  
 W poniższym przykładzie `price` element pierwszego `book` elementu `contosoBooks.xml` plik zostanie usunięty przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody. Pozycja <xref:System.Xml.XPath.XPathNavigator> obiektu po `price` usuwany element znajduje się na element nadrzędny `book` elementu.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Usunięcie węzła atrybutu  
 Atrybut węzły są usuwane z dokumentu XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.  
  
 Po usunięciu węzła atrybutu nie jest już dostępny od węzła głównego z <xref:System.Xml.XmlDocument> obiektu i <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się na elemencie nadrzędnym.  
  
#### <a name="default-attributes"></a>Domyślne atrybuty  
 Niezależnie od metody umożliwia usuwanie atrybutów ma ograniczeń specjalnych na usuwanie atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji DTD lub schemat XML dokumentu XML. Nie można usunąć atrybutów domyślnych, chyba że element, do którego należą również zostanie usunięty. Domyślne atrybuty zawsze znajdują się dla elementów, które mają domyślne atrybuty został zadeklarowany i w związku z tym usuwanie wyników atrybut domyślny atrybut zastępczy wstawiane do elementu i zainicjować przy użyciu wartości domyślnej, który został zadeklarowany.  
  
## <a name="removing-values"></a>Usuwanie wartości  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, aby usunąć bez typu i wpisane wartości z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Usuwanie nieuwzględniające typów wartości  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia bez typu `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na. Przekazywanie pusty ciąg, aby <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda usuwa wartość bieżącego węzła.  
  
 Poniższy przykład umożliwia usunięcie wartości `price` element pierwszego `book` element w `contosoBooks.xml` plik za pomocą <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Usuwanie typu wartości  
 Gdy typ węzła to proste schematu W3C XML typ, nowa wartość wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przed ma wartość metody zostaje sprawdzony pod kątem aspekty typu prostego. Jeśli nowa wartość nie jest prawidłowa dla typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wygenerowanie wyjątku. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Również nie mogą być przekazywane metody `null` jako parametr. W związku z tym usuwanie wartość węzła typu muszą być zgodne z typem schematu węzła.  
  
 Poniższy przykład umożliwia usunięcie wartości `price` element pierwszego `book` element `contosoBooks.xml` plik za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody przez ustawienie wartości `0`. Wartość węzła nie jest usuwany, ale została usunięta cen książki zgodnie z jego typu danych `xs:decimal`.  
  
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
  
## <a name="namespace-nodes"></a>Namespace węzłów  
 Nie można usunąć węzłów Namespace z <xref:System.Xml.XmlDocument> obiektu. Próbuje usunąć węzłów przestrzeni nazw przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda powoduje wygenerowanie wyjątku.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości OuterXml i InnerXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy Zmień adiustację XML węzłów <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na przy użyciu analizowanej zawartości danego XML `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na oraz bieżącego węzła.  
  
 Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości mogą służyć do usuwania węzłów i wartości z dokumentu XML. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby zmodyfikować węzłów, zobacz [zmodyfikować danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiekt jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian w <xref:System.Xml.XmlDocument> obiektów, zobacz [zapisywania i zapisywanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
