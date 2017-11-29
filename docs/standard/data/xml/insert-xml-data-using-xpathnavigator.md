---
title: "Wstawianie danych XML przy użyciu parametrem XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34151590a14c48c0a84677f2d7cae662291edf40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Wstawianie danych XML przy użyciu parametrem XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod służy do wstawiania podrzędnych, węzłów atrybutu i rodzeństwa w dokumencie XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są tylko do odczytu i próby użycia metody edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> obiektu powoduje <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu można edytować <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Wstawianie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody do wstawienia podrzędnych, węzłów atrybutu i rodzeństwa w dokumencie XML. Te metody umożliwiają wstawianie węzły i atrybutów w różnych lokalizacjach w stosunku do bieżącego położenia <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.  
  
### <a name="inserting-sibling-nodes"></a>Wstawianie węzły równorzędne  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłami tego samego poziomu.  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Te metody Wstaw węzłami tego samego poziomu przed i po węzeł <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody jest przeciążona i zaakceptować `string`, <xref:System.Xml.XmlReader> obiekt, lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł równorzędny do dodania jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłami tego samego poziomu.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody Wstaw węzeł równorzędny pojedynczego przed i po węzeł <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na przy użyciu prefiksu przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy `pages` element dodaje się przed `price` pierwszym elementem podrzędnym `book` element `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentacji.  
  
### <a name="inserting-child-nodes"></a>Wstawianie węzłów podrzędnych  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów podrzędnych.  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Te metody dołączyć i dołączy węzłów podrzędnych do końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.  
  
 Takie jak metody w sekcji "Wstawianie węzłami tego samego poziomu" <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody `string`, <xref:System.Xml.XmlReader> obiekt, lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzła podrzędnego do dodania jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłów podrzędnych.  
  
 Chce także metody w sekcji "Wstawianie węzłami tego samego poziomu" <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody Wstaw węzeł pojedynczy element potomny do końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie w użyciu Prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy `pages` elementu podrzędnego jest dołączany do listy elementów podrzędnych pierwszego `book` element `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentacji.  
  
### <a name="inserting-attribute-nodes"></a>Wstawianie atrybutów węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów atrybutu.  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Te metody wstawiania węzłów atrybutu w węźle elementu <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda tworzy węzła atrybutu w węźle elementu <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na przy użyciu prefiksu przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda zwraca <xref:System.Xml.XmlWriter> obiektu służy do wstawiania węzłów atrybutu.  
  
 W poniższym przykładzie, nowe `discount` i `currency` atrybuty są tworzone na `price` pierwszym elementem podrzędnym `book` element `contosoBooks.xml` plik za pomocą <xref:System.Xml.XmlWriter> obiektu zwróconego z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentacji.  
  
## <a name="copying-nodes"></a>Kopiowanie węzłów  
 W niektórych przypadkach można wypełnić dokumentu XML z zawartością z innego dokumentu XML. Zarówno <xref:System.Xml.XPath.XPathNavigator> klasy i <xref:System.Xml.XmlWriter> klasy można kopiować węzłów do <xref:System.Xml.XmlDocument> obiektu z istniejącego <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy mają przeciążenia, które mogą akceptować <xref:System.Xml.XPath.XPathNavigator> obiektu lub <xref:System.Xml.XmlReader> obiekt jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Metody <xref:System.Xml.XmlWriter> klasa ma przeciążeń, które może przyjąć <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
 Poniższy przykładowy kod kopiuje wszystkie `book` elementy z jednego dokumentu.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a>Wstawianie wartości  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metod do wstawienia wartości dla węzła do <xref:System.Xml.XmlDocument> obiektu.  
  
### <a name="inserting-untyped-values"></a>Wstawianie nieuwzględniające typów wartości  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia bez typu `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na. Wartość jest wstawiany bez dowolnego typu lub bez sprawdzenia, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli informacje o schemacie są dostępne.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Wstawianie wpisywane wartości  
 Gdy typ węzła to proste schematu W3C XML typ, nowa wartość wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przed ma wartość metody zostaje sprawdzony pod kątem aspekty typu prostego. Jeśli nowa wartość nie jest prawidłowa dla typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wygenerowanie wyjątku.  
  
 Poniższy przykład próbuje zmienić wartość `price` element pierwszego `book` element `contosoBooks.xml` pliku na <xref:System.DateTime> wartość. Ponieważ typ schematu XML `price` element jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` pliki, powoduje to wygenerowanie wyjątku.  
  
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
  
navigator.SetTypedValue(DateTime.Now)  
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
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości OuterXml i InnerXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy Zmień adiustację XML węzłów <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na przy użyciu analizowanej zawartości danego XML `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na oraz bieżącego węzła.  
  
 Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości mogą służyć do wstawienia wartości i węzły w dokumencie XML. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby wstawić węzły i wartości, zobacz [zmodyfikować danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace i XML: lang — konflikty  
 Niektóre konflikty związane z zakresu przestrzeni nazw i `xml:lang` deklaracje może wystąpić, gdy Wstawianie danych XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy, która <xref:System.Xml.XmlReader>obiektów jako parametry.  
  
 Poniżej przedstawiono możliwe przestrzeń nazw powoduje konflikt.  
  
-   W przypadku przestrzeni nazw w zakresie w <xref:System.Xml.XmlReader> kontekst obiektu, gdy prefiks do mapowania identyfikatora URI przestrzeni nazw nie znajduje się w <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu nowego deklaracja przestrzeni nazw jest dodawana do nowo wstawionej węzła.  
  
-   Jeśli w tym samym identyfikatorem URI przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale ma inny prefiks mapowane w obu kontekstach, nowe deklaracja przestrzeni nazw jest dodawana do nowo wstawionej węzła z prefiksem i pobierane z identyfikatorem URI przestrzeni nazw <xref:System.Xml.XmlReader> obiektu.  
  
-   Jeśli ten sam prefiks przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale ma inny identyfikator URI przestrzeni nazw jest zamapowana do niego w obu kontekstach, nowe deklaracji przestrzeni nazw jest dodawany do nowo wstawionej węzła który ponownie deklaruje tego prefiksu przestrzeni nazw z identyfikatora URI <xref:System.Xml.XmlReader> obiektu.  
  
-   Jeśli prefiks, jak również identyfikator URI przestrzeni nazw w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu jest taki sam, nie nowe deklaracja przestrzeni nazw jest dodawana do nowo wstawionej węzła.  
  
> [!NOTE]
>  Opis powyżej mają zastosowanie również do deklaracji przestrzeni nazw z pustą `string` jako prefiksu (na przykład deklarację domyślnej przestrzeni nazw).  
  
 Poniżej przedstawiono możliwe `xml:lang` konflikty.  
  
-   W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XmlReader> obiektu kontekstu, ale nie <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do nowo wstawionej węzła.  
  
-   W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale każda ma inną wartość, `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do nowo wstawionej węzła.  
  
-   W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale każda z taką samą wartość, żadna nowa `xml:lang` na nowo wstawionej węzła jest dodawany atrybut.  
  
-   W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale nie istnieje w <xref:System.Xml.XmlReader> obiektu kontekstu, nie `xml:lang` nowo wstawionej węzła jest dodawany atrybut.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Wstawianie węzłów o XmlWriter  
 Metody używane do wstawiania węzłów podrzędnych i atrybut rodzeństwa opisany w sekcji "Wstawianie węzłów i wartości" jest przeciążony. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy powrotu <xref:System.Xml.XmlWriter> obiektu służy do wstawiania węzłów.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nieobsługiwany parametr XmlWriter metody  
 Nie wszystkie metody używane do zapisywania informacji o dokumentu XML przy użyciu <xref:System.Xml.XmlWriter> klasy są obsługiwane przez <xref:System.Xml.XPath.XPathNavigator> klasy z powodu różnic między XPath modelu danych i modelu DOM (Document Object).  
  
 W poniższej tabeli opisano <xref:System.Xml.XmlWriter> nie są obsługiwane przez metody klasy <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Zgłasza wyjątek <xref:System.NotSupportedException> wyjątku.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorowane na poziomie głównym i zgłasza <xref:System.NotSupportedException> wyjątek, jeśli wywoływane na innym poziomie dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metoda odpowiednik znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metoda odpowiednik znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metoda odpowiednik znaku lub znaków.|  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlWriter> , zobacz <xref:System.Xml.XmlWriter> klasy dokumentacji.  
  
### <a name="multiple-xmlwriter-objects"></a>Wiele obiektów XmlWriter  
 Użytkownik może mieć wielu <xref:System.Xml.XPath.XPathNavigator> obiektów wskazujący różnych części XML dokumentu po otwarciu co najmniej jeden <xref:System.Xml.XmlWriter> obiektów. Wiele <xref:System.Xml.XmlWriter> obiektów są dozwolone i obsługiwane w scenariuszach jednowątkowy.  
  
 Poniżej przedstawiono ważne uwagi, które należy wziąć pod uwagę przy użyciu wielu <xref:System.Xml.XmlWriter> obiektów.  
  
-   Fragmenty XML napisane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do pliku XML dokumentu, kiedy <xref:System.Xml.XmlWriter.Close%2A> metody każdego <xref:System.Xml.XmlWriter> nosi nazwę obiektu. Do tego momentu <xref:System.Xml.XmlWriter> obiektu zapisuje odłączonego fragmentu. Jeśli operacja jest wykonywana na dokument XML, wszystkie fragmenty zapisywana przez <xref:System.Xml.XmlWriter> obiekt przed <xref:System.Xml.XmlWriter.Close%2A> została wywołana, nie dotyczy.  
  
-   Jeżeli istnieje otwarty <xref:System.Xml.XmlWriter> obiektu, w szczególności poddrzewo XML i że poddrzewo zostanie usunięty, <xref:System.Xml.XmlWriter> obiektu nadal mogą dodawać do drzewa podrzędnego. Poddrzewo staje się po prostu usunięto fragmentu.  
  
-   Jeśli wiele <xref:System.Xml.XmlWriter> obiektów są otwarte w tym samym punkcie w dokumencie XML, są dodawane do dokumentu XML w kolejności, w którym <xref:System.Xml.XmlWriter> obiekty są zamknięte, nie w kolejności, w której zostały otwarte.  
  
 Poniższy przykład tworzy <xref:System.Xml.XmlDocument> obiektów, tworzy <xref:System.Xml.XPath.XPathNavigator> obiektu, a następnie używa <xref:System.Xml.XmlWriter> obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodę w celu utworzenia struktury pierwszej książki w `books.xml` pliku. Przykład następnie zapisuje go jako `book.xml` pliku.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiekt jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian w <xref:System.Xml.XmlDocument> obiektów, zobacz [zapisywania i zapisywanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Modyfikowanie danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 [Usuwanie danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
