---
title: Wstawianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1dbe1a709f7c1b527a1754ab943a0a10ff52c6e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289190"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Wstawianie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Klasa zawiera zestaw metod służących do wstawiania węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, że jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość musi być `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy użyciu <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasę są tylko do odczytu, a każda próba użycia metod edycji <xref:System.Xml.XPath.XPathNavigator> obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt daje w wyniku <xref:System.NotSupportedException> .  
  
 Aby uzyskać więcej informacji na temat tworzenia edytowalnych <xref:System.Xml.XPath.XPathNavigator> obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Wstawianie węzłów  
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera metody umożliwiające Wstawianie węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Te metody umożliwiają wstawianie węzłów i atrybutów w różnych lokalizacjach w odniesieniu do bieżącego położenia <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.  
  
### <a name="inserting-sibling-nodes"></a>Wstawianie węzłów równorzędnych  
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera następujące metody wstawiania węzłów równorzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Te metody wstawiają węzły równorzędne przed i po węźle, <xref:System.Xml.XPath.XPathNavigator> w którym jest obecnie umieszczony obiekt.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Metody i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> są przeciążone i akceptują `string` , <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł równorzędny, aby dodać jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłów elementów równorzędnych.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>Metody i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> wstawiają pojedynczy węzeł równorzędny przed i po węźle, <xref:System.Xml.XPath.XPathNavigator> w którym aktualnie znajduje się obiekt, przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy `pages` element jest wstawiany przed `price` elementem podrzędnym pierwszego `book` elementu w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metodach, i znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.  
  
### <a name="inserting-child-nodes"></a>Wstawianie węzłów podrzędnych  
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera następujące metody wstawiania węzłów podrzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Te metody dołączą i dołączają węzły podrzędne do końca i początku listy węzłów podrzędnych w węźle, <xref:System.Xml.XPath.XPathNavigator> w którym znajduje się obiekt.  
  
 Podobnie jak metody w sekcji "Wstawianie węzłów równorzędnych", <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody akceptują `string` , <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł podrzędny, aby dodać jako parametry. Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłów podrzędnych.  
  
 Podobnie jak metody w sekcji "Wstawianie węzłów równorzędnych", <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody i umożliwiają wstawianie jednego węzła podrzędnego do końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy `pages` element podrzędny jest dołączany do listy elementów podrzędnych pierwszego `book` elementu w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metodach, i znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.  
  
### <a name="inserting-attribute-nodes"></a>Wstawianie węzłów atrybutów  
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera następujące metody wstawiania węzłów atrybutów.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Te metody wstawiają węzły atrybutów w węźle elementu, <xref:System.Xml.XPath.XPathNavigator> w którym obiekt jest obecnie umieszczony. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Metoda tworzy węzeł atrybutu w węźle elementu <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>Metoda zwraca <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłów atrybutów.  
  
 W poniższym przykładzie nowe `discount` i `currency` atrybuty są tworzone w `price` elemencie podrzędnym pierwszego `book` elementu w `contosoBooks.xml` pliku przy użyciu <xref:System.Xml.XmlWriter> obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metodę.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metodach i znajduje się w dokumentacji dotyczącej <xref:System.Xml.XPath.XPathNavigator> klas.  
  
## <a name="copying-nodes"></a>Kopiowanie węzłów  
 W niektórych przypadkach może być konieczne wypełnienie dokumentu XML zawartością z innego dokumentu XML. Zarówno <xref:System.Xml.XPath.XPathNavigator> Klasa, jak i <xref:System.Xml.XmlWriter> Klasa mogą kopiować węzły do <xref:System.Xml.XmlDocument> obiektu z istniejącego <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> , <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator> klasy All mają przeciążenia, które mogą akceptować <xref:System.Xml.XPath.XPathNavigator> obiekt lub <xref:System.Xml.XmlReader> obiekt jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A>Metoda <xref:System.Xml.XmlWriter> klasy ma przeciążenia, które mogą akceptować <xref:System.Xml.XmlNode> <xref:System.Xml.XmlReader> obiekt,, lub <xref:System.Xml.XPath.XPathNavigator> .  
  
 Poniższy przykład kopiuje wszystkie `book` elementy z jednego dokumentu do drugiego.  
  
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
 <xref:System.Xml.XPath.XPathNavigator>Klasa zawiera <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody i, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> które umożliwiają wstawianie wartości dla węzła do <xref:System.Xml.XmlDocument> obiektu.  
  
### <a name="inserting-untyped-values"></a>Wstawianie wartości niewpisanych  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metoda po prostu wstawia wartość bez typu jako `string` parametr jako wartość węzła, <xref:System.Xml.XPath.XPathNavigator> na którym znajduje się obiekt. Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jest używana do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Wstawianie wpisanych wartości  
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger` ), powoduje wyjątek.  
  
 Poniższy przykład próbuje zmienić wartość `price` elementu pierwszego `book` elementu w `contosoBooks.xml` pliku na <xref:System.DateTime> wartość. Ponieważ typ schematu XML `price` elementu jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` plikach, spowoduje to wyjątek.  
  
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
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości InnerXml i OuterXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Właściwości i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> <xref:System.Xml.XPath.XPathNavigator> klasy zmieniają znaczniki XML w węzłach, <xref:System.Xml.XPath.XPathNavigator> w których obiekt jest obecnie umieszczony.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Właściwość zmienia znaczniki XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string` . Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML węzłów podrzędnych, <xref:System.Xml.XPath.XPathNavigator> w których obiekt jest obecnie umieszczony, a także bieżący węzeł.  
  
 Poza metodami opisanymi w tym temacie, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości i mogą służyć do wstawiania węzłów i wartości w dokumencie XML. Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> używania <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości i do wstawiania węzłów i wartości, zobacz temat [modyfikowanie danych XML przy użyciu elementu XPathNavigator](modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="namespace-and-xmllang-conflicts"></a>Przestrzeń nazw i XML: konflikty lang  
 Niektóre konflikty związane z zakresem przestrzeni nazw i `xml:lang` deklaracji mogą wystąpić podczas wstawiania danych XML przy <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> użyciu <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metod, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i klasy, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> które przyjmują <xref:System.Xml.XmlReader> obiekty jako parametry.  
  
 Poniżej wymieniono potencjalne konflikty przestrzeni nazw.  
  
- Jeśli w kontekście obiektu znajduje się przestrzeń nazw, w <xref:System.Xml.XmlReader> której prefiks do mapowania identyfikatora URI przestrzeni nazw nie znajduje się w <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, zostanie dodana nowa Deklaracja przestrzeni nazw do nowo wstawionego węzła.  
  
- Jeśli ten sam identyfikator URI przestrzeni nazw znajduje się w zakresie zarówno w <xref:System.Xml.XmlReader> kontekście obiektu, jak i w <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, ale ma inny prefiks mapowany w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła z prefiksem i identyfikatorem URI przestrzeni nazw pobranym z <xref:System.Xml.XmlReader> obiektu.  
  
- Jeśli ten sam prefiks przestrzeni nazw znajduje się w zakresie zarówno w <xref:System.Xml.XmlReader> kontekście obiektu, jak i <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, ale ma inny identyfikator URI przestrzeni nazw mapowany do niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, który ponownie deklaruje ten prefiks przy użyciu identyfikatora URI przestrzeni nazw pobranego z <xref:System.Xml.XmlReader> obiektu.  
  
- Jeśli prefiks oraz identyfikator URI przestrzeni nazw w <xref:System.Xml.XmlReader> kontekście obiektu i <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu są takie same, do nowo wstawionego węzła nie zostanie dodana żadna Nowa deklaracja przestrzeni nazw.  
  
> [!NOTE]
> Powyższy opis dotyczy również deklaracji przestrzeni nazw z pustym `string` prefiksem (na przykład deklaracji domyślnej przestrzeni nazw).  
  
 Możliwe są następujące `xml:lang` konflikty.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie w <xref:System.Xml.XmlReader> kontekście obiektu, ale nie w <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawionego węzła.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie zarówno w <xref:System.Xml.XmlReader> kontekście obiektu, jak i <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, ale każdy z nich ma inną wartość, `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawionego węzła.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie zarówno w <xref:System.Xml.XmlReader> kontekście obiektu, jak i <xref:System.Xml.XPath.XPathNavigator> kontekstu obiektu, ale każdy z tą samą wartością, żaden nowy `xml:lang` atrybut nie zostanie dodany do nowo wstawionego węzła.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie w <xref:System.Xml.XPath.XPathNavigator> kontekście obiektu, ale żaden istniejący w <xref:System.Xml.XmlReader> kontekście obiektu nie `xml:lang` zostanie dodany do nowo wstawionego węzła.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Wstawianie węzłów z XmlWriter  
 Metody służące do wstawiania elementów równorzędnych, podrzędnych i atrybutów, które opisano w sekcji "Wstawianie węzłów i wartości" są przeciążone. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> , <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> <xref:System.Xml.XPath.XPathNavigator> klasy zwracają <xref:System.Xml.XmlWriter> obiekt używany do wstawiania węzłów.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nieobsługiwane metody XmlWriter  
 Nie wszystkie metody służące do zapisywania informacji w dokumencie XML przy użyciu <xref:System.Xml.XmlWriter> klasy są obsługiwane przez <xref:System.Xml.XPath.XPathNavigator> klasę z powodu różnic między modelem danych XPath a Document Object Model (dom).  
  
 W poniższej tabeli opisano <xref:System.Xml.XmlWriter> metody klasy, które nie są obsługiwane przez <xref:System.Xml.XPath.XPathNavigator> klasę.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Zgłasza <xref:System.NotSupportedException> wyjątek.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorowany na poziomie głównym i zgłasza <xref:System.NotSupportedException> wyjątek, jeśli jest wywoływana na dowolnym innym poziomie dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
  
 Więcej informacji o klasie można <xref:System.Xml.XmlWriter> znaleźć w dokumentacji dotyczącej <xref:System.Xml.XmlWriter> klas.  
  
### <a name="multiple-xmlwriter-objects"></a>Wiele obiektów XmlWriter  
 Istnieje możliwość, że wiele <xref:System.Xml.XPath.XPathNavigator> obiektów wskazuje różne części dokumentu XML z co najmniej jednym otwartym <xref:System.Xml.XmlWriter> obiektem. Wiele <xref:System.Xml.XmlWriter> obiektów jest dozwolonych i obsługiwanych w scenariuszach wielowątkowych.  
  
 Poniżej znajdują się ważne uwagi, które należy wziąć pod uwagę podczas korzystania z wielu <xref:System.Xml.XmlWriter> obiektów.  
  
- Fragmenty XML zapisywane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do dokumentu XML, gdy <xref:System.Xml.XmlWriter.Close%2A> wywoływana jest metoda każdego <xref:System.Xml.XmlWriter> obiektu. Do tego momentu <xref:System.Xml.XmlWriter> obiekt zapisuje odłączony fragment. Jeśli operacja jest wykonywana na dokumencie XML, nie ma to wpływ na wszystkie fragmenty, które są zapisywane przez <xref:System.Xml.XmlWriter> obiekt przed <xref:System.Xml.XmlWriter.Close%2A> wywołaniem.  
  
- Jeśli istnieje otwarty <xref:System.Xml.XmlWriter> obiekt w określonym poddrzewie XML i że poddrzewo zostanie usunięte, <xref:System.Xml.XmlWriter> obiekt może nadal dodawać do poddrzewa. Poddrzewo po prostu zostaje usuniętym fragmentem.  
  
- Jeśli wiele <xref:System.Xml.XmlWriter> obiektów jest otwartych w tym samym punkcie dokumentu XML, są one dodawane do dokumentu XML w kolejności, w której <xref:System.Xml.XmlWriter> obiekty są zamknięte, a nie w kolejności, w jakiej zostały otwarte.  
  
 Poniższy przykład tworzy <xref:System.Xml.XmlDocument> obiekt, tworzy <xref:System.Xml.XPath.XPathNavigator> obiekt, a następnie używa <xref:System.Xml.XmlWriter> obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodę w celu utworzenia struktury pierwszej książki w `books.xml` pliku. Przykład zapisuje go jako `book.xml` plik.  
  
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
 Zapisywanie zmian wprowadzonych <xref:System.Xml.XmlDocument> w obiekcie w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](modify-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](remove-xml-data-using-xpathnavigator.md)
