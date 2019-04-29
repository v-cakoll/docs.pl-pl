---
title: Wstawianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 224e4f3db31e4818833eb8411f44f547538534fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650248"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Wstawianie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które służy do wstawiania element równorzędny, podrzędne i węzłów atrybutu w dokumencie XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być niemożliwa, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są przeznaczone tylko do odczytu i dowolne próba należy użyć metod edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> skutkuje obiektu <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu edytowalne <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Wstawianie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody, aby wstawić element równorzędny, podrzędne i węzłów atrybutu w dokumencie XML. Te metody umożliwiają wstawianie węzłów i atrybuty w różnych lokalizacjach w odniesieniu do bieżącego położenia obiektu <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.  
  
### <a name="inserting-sibling-nodes"></a>Wstawianie węzłów elementów równorzędnych  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów elementów równorzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Te metody insert węzłów elementów równorzędnych, przed i po węźle <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody są przeciążone i zaakceptuj `string`, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiekt, który zawiera węzeł równorzędny do dodania jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów elementów równorzędnych.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody Wstaw węzeł równorzędne jednym przed i po węźle <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowej `pages` element jest wstawiany przed `price` pierwszy element podrzędny `book` element `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.  
  
### <a name="inserting-child-nodes"></a>Wstawianie węzłów podrzędnych  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów podrzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Te metody dołączyć i Dodaj węzły podrzędne końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.  
  
 Takie jak metody w sekcji "Wstawianie węzłów elementów równorzędnych" <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> akceptować metod `string`, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiekt, który zawiera węzeł podrzędny do dodania jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów podrzędnych.  
  
 Metody w sekcji "Wstawianie węzłów elementów równorzędnych" się także podobać <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody Wstawianie pojedynczy element podrzędny węzła do końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z Prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy `pages` elementu podrzędnego jest dołączany do listy elementów podrzędnych pierwszego `book` element `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.  
  
### <a name="inserting-attribute-nodes"></a>Wstawianie węzłów atrybutu  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów atrybutu.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Te metody insert węzłów atrybutu w węźle element <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda tworzy węzeł atrybutu na węzeł elementu <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda zwraca <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów atrybutu.  
  
 W poniższym przykładzie nowy `discount` i `currency` atrybuty są tworzone na `price` pierwszy element podrzędny `book` element `contosoBooks.xml` plików przy użyciu <xref:System.Xml.XmlWriter> obiekt zwracany z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.  
  
## <a name="copying-nodes"></a>Kopiowanie węzłów  
 W niektórych przypadkach można wypełnić dokumentu XML z zawartością z innego dokumentu XML. Zarówno <xref:System.Xml.XPath.XPathNavigator> klasy i <xref:System.Xml.XmlWriter> klasy można skopiować węzłów <xref:System.Xml.XmlDocument> obiektu z istniejącego <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy wszystkie mają przeciążenia, które mogą akceptować <xref:System.Xml.XPath.XPathNavigator> obiektu lub <xref:System.Xml.XmlReader> obiektu jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Metody <xref:System.Xml.XmlWriter> klasa ma przeciążenia, które mogą akceptować <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
 Poniższy przykład kopiuje wszystkie `book` elementy z jednego dokumentu.  
  
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
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody do wstawienia wartości dla węzła do <xref:System.Xml.XmlDocument> obiektu.  
  
### <a name="inserting-untyped-values"></a>Wstawianie wartości bez typu  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia nietypizowane `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na. Wartość jest wstawiany bez dowolnego typu lub bez weryfikacji, nowa wartość jest nieprawidłowa według typu węzła, jeśli informacje schematu są dostępne.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Wstawianie wartości Typizowane  
 Gdy typ węzła jest schematu XML W3C prosty typ, nowej wartości, które są wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody jest sprawdzana względem aspekty typu prostego, zanim ma wartość. Jeśli nowa wartość nie jest nieprawidłowa według typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wyjątek.  
  
 Poniższy przykład podejmie próbę Zmień wartość właściwości `price` element pierwszego `book` element `contosoBooks.xml` plik <xref:System.DateTime> wartość. Ponieważ typ schematu XML `price` element jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` pliki, powoduje to wyjątek.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości OuterXml i elementu  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zmienić węzłów znaczniki XML <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> przeanalizowany zawartość XML danego obiektu aktualnie jest ustawiony na `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiektu aktualnie jest ustawiony na oraz bieżącego węzła.  
  
 Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości może służyć do wstawienia wartości i węzły w dokumencie XML. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby wstawić węzłów i wartości, zobacz [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace i konfliktów XML: lang  
 Niektóre konflikty związane z zakresu przestrzeni nazw i `xml:lang` deklaracje mogą wystąpić podczas wstawiania danych XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy, które umożliwiają wykorzystywanie <xref:System.Xml.XmlReader>obiektów jako parametrów.  
  
 Poniżej przedstawiono możliwe przestrzeń nazw powoduje konflikt.  
  
- W przypadku przestrzeni nazw w zakresie w ramach <xref:System.Xml.XmlReader> obiektu kontekstu, w którym długości prefiksu do mapowania identyfikatora URI przestrzeni nazw nie znajduje się w <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, nowe deklaracji przestrzeni nazw jest dodawany do nowo wstawionej węzła.  
  
- Jeśli ten sam identyfikator URI przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale ma inny prefiks mapowane w obu kontekstach, nowe deklaracji przestrzeni nazw jest dodawany do nowo wstawionej węzła, z prefiksem i pobierane z identyfikatora URI obszaru nazw <xref:System.Xml.XmlReader> obiektu.  
  
- Jeśli ten sam prefiks przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale ma inny identyfikator URI przestrzeni nazw jest mapowany do niego w obu kontekstów, deklarację przestrzeni nazw nowych zostaje dodany do węzła nowo wstawionej który ponownie deklaruje tego prefiksu z przestrzenią nazw identyfikatora URI z <xref:System.Xml.XmlReader> obiektu.  
  
- Jeśli prefiks, a także identyfikator URI przestrzeni nazw w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu jest taka sama, nie nowe deklaracja przestrzeni nazw jest dodawana do nowo wstawionej węzła.  
  
> [!NOTE]
>  Powyższy opis dotyczy także deklaracje przestrzeni nazw z pustym `string` jako prefiksu (na przykład deklarację domyślnej przestrzeni nazw).  
  
 Poniżej przedstawiono możliwe `xml:lang` konflikty.  
  
- W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XmlReader> kontekst obiektu, ale nie <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do nowo wstawionej węzła.  
  
- W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale każdy ma inną wartość `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do węzeł nowo wstawione.  
  
- W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale każdy z taką samą wartość żadnego nowego `xml:lang` na nowo wstawionej węzła jest dodawany atrybut.  
  
- W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale nie istnieje w <xref:System.Xml.XmlReader> obiektu kontekstu, nie `xml:lang` atrybutu jest dodawany do nowo wstawionej węzła.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Wstawianie węzłów za pomocą XmlWriter  
 Są przeciążone metody używane do wstawiania węzłów podrzędnych i atrybutów rodzeństwa opisane w sekcji "Wstawianie węzłów i Values". <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy zwrócenia <xref:System.Xml.XmlWriter> obiektu służy do wstawiania węzłów.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nieobsługiwany parametr XmlWriter metody  
 Nie wszystkie metody używane do zapisywania dokumentów XML za pomocą informacji <xref:System.Xml.XmlWriter> klasy są obsługiwane przez <xref:System.Xml.XPath.XPathNavigator> klasy z powodu różnic między modelu danych XPath i Document Object Model (DOM).  
  
 W poniższej tabeli opisano <xref:System.Xml.XmlWriter> nie są obsługiwane przez metody klasy <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Zgłasza <xref:System.NotSupportedException> wyjątku.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorowane na poziomie głównym i zgłasza <xref:System.NotSupportedException> wyjątek, jeśli wywołano na dowolnym poziomie, w dokumencie XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.|  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlWriter> klasy, zobacz <xref:System.Xml.XmlWriter> klasy dokumentację referencyjną.  
  
### <a name="multiple-xmlwriter-objects"></a>Wiele obiektów XmlWriter  
 Użytkownik może mieć wielu <xref:System.Xml.XPath.XPathNavigator> obiekty, które wskazuje do różnych części pliku XML dokumentu z co najmniej jeden open <xref:System.Xml.XmlWriter> obiektów. Wiele <xref:System.Xml.XmlWriter> obiekty są dozwolone i obsługiwane w scenariuszach apartamentem.  
  
 Poniżej przedstawiono ważne uwagi, które należy wziąć pod uwagę przy użyciu wielu <xref:System.Xml.XmlWriter> obiektów.  
  
- Fragmenty XML, napisane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do pliku XML dokumentu, gdy <xref:System.Xml.XmlWriter.Close%2A> metoda każdego <xref:System.Xml.XmlWriter> nosi nazwę obiektu. Do tego momentu <xref:System.Xml.XmlWriter> obiekt zapisuje odłączonego fragmentu. Jeśli operacja jest wykonywana na dokumencie XML, wszystkie fragmenty są zapisywane przez <xref:System.Xml.XmlWriter> obiekt przed <xref:System.Xml.XmlWriter.Close%2A> została wywołana, nie ulegają zmianom.  
  
- W przypadku otwartą <xref:System.Xml.XmlWriter> obiektu w określonej poddrzewo XML i że poddrzewo zostanie usunięty, <xref:System.Xml.XmlWriter> obiekt nadal może dodawać do poddrzewa. Poddrzewo staje się po prostu usuniętych fragmentu.  
  
- Jeśli wiele <xref:System.Xml.XmlWriter> obiektów są otwarte w tym samym punkcie w dokumencie XML, są dodawane do dokumentu XML w kolejności, w którym <xref:System.Xml.XmlWriter> obiekty zostały zamknięte, nie w kolejności, w jakiej zostały otwarte.  
  
 Poniższy przykład tworzy <xref:System.Xml.XmlDocument> obiekt, tworzy <xref:System.Xml.XPath.XPathNavigator> obiektu, a następnie używa <xref:System.Xml.XmlWriter> obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodą tworzenia struktury pierwszej książki w `books.xml` pliku. Przykład następnie zapisuje ją jako `book.xml` pliku.  
  
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
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiektu jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian <xref:System.Xml.XmlDocument> obiektu, zobacz [zapisywania i zapisywania dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
