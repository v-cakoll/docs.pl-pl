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
ms.openlocfilehash: 4ff9232272124c8706e64162d096eced8640c806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966955"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Wstawianie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod służących do wstawiania węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> że jego właściwość `true`musi być.  
  
 <xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy <xref:System.Xml.XmlDocument.CreateNavigator%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasę są tylko do odczytu, a każda próba użycia metod <xref:System.Xml.XPath.XPathNavigator> edycji obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt daje w wyniku <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator> tworzenia edytowalnych obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Wstawianie węzłów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera metody umożliwiające Wstawianie węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Te metody umożliwiają wstawianie węzłów i atrybutów w różnych lokalizacjach w odniesieniu do bieżącego położenia <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.  
  
### <a name="inserting-sibling-nodes"></a>Wstawianie węzłów równorzędnych  
 <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów równorzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Te metody wstawiają węzły równorzędne przed i po węźle <xref:System.Xml.XPath.XPathNavigator> , w którym jest obecnie umieszczony obiekt.  
  
 <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> sąprzeciążoneiakceptują,obiektlubobiektzawierającywęzeł`string`równorzędny, aby dodać jako parametry. Obie metody zwracają <xref:System.Xml.XmlWriter> również obiekt używany do wstawiania węzłów elementów równorzędnych.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> <xref:System.Xml.XPath.XPathNavigator> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> wstawiają pojedynczy węzeł równorzędny przed i po węźle, w którym aktualnie znajduje się obiekt, przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.  
  
 `pages` W poniższym przykładzie nowy element jest wstawiany `price` przed elementem podrzędnym pierwszego `book` elementu w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>informacji o metodach <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> , <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.  
  
### <a name="inserting-child-nodes"></a>Wstawianie węzłów podrzędnych  
 <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów podrzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Te metody dołączą i dołączają węzły podrzędne do końca i początku listy węzłów podrzędnych w węźle <xref:System.Xml.XPath.XPathNavigator> , w którym znajduje się obiekt.  
  
 Podobnie jak metody w sekcji "Wstawianie węzłów <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> równorzędnych", a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody akceptują `string`, <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł podrzędny, aby dodać jako parametry. Obie metody zwracają <xref:System.Xml.XmlWriter> również obiekt używany do wstawiania węzłów podrzędnych.  
  
 Podobnie jak w przypadku metod w sekcji <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> "Wstawianie węzłów równorzędnych" i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody wstawiania pojedynczego węzła podrzędnego do końca i początku listy <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych węzła obiekt jest obecnie umieszczony przy użyciu prefiks przestrzeni nazw, nazwa lokalna, identyfikator URI przestrzeni nazw oraz wartość określona jako parametry.  
  
 W poniższym przykładzie nowy `pages` element podrzędny jest dołączany do listy elementów podrzędnych pierwszego `book` elementu w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>informacji o metodach <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> , <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.  
  
### <a name="inserting-attribute-nodes"></a>Wstawianie węzłów atrybutów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów atrybutów.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Te metody wstawiają węzły atrybutów w węźle elementu, <xref:System.Xml.XPath.XPathNavigator> w którym obiekt jest obecnie umieszczony. Metoda tworzy węzeł atrybutu w <xref:System.Xml.XPath.XPathNavigator> węźle elementu obiekt jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda<xref:System.Xml.XmlWriter> zwraca obiekt używany do wstawiania węzłów atrybutów.  
  
 W `discount` poniższym przykładzie nowe i `currency` `price` atrybuty są tworzone w elemencie `contosoBooks.xml` podrzędnym pierwszego `book` elementu w pliku przy użyciu <xref:System.Xml.XmlWriter> obiektu zwróconego z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Method.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> metodach i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> znajduje się <xref:System.Xml.XPath.XPathNavigator> w dokumentacji dotyczącej klas.  
  
## <a name="copying-nodes"></a>Kopiowanie węzłów  
 W niektórych przypadkach może być konieczne wypełnienie dokumentu XML zawartością z innego dokumentu XML. <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlDocument> Zarówno Klasa, jak i Klasamogąkopiowaćwęzłydoobiektuzistniejącegoobiektulubobiektu.<xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> Metody,<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ,<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>i <xref:System.Xml.XmlReader> klasyAllmająprzeciążenia,któremogąakceptowaćobiektlubobiektjakoparametr.<xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader>Metoda klasy ma przeciążenia, które mogą akceptować obiekt ,,lub.<xref:System.Xml.XmlNode> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.WriteNode%2A>  
  
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
 Klasa zawiera metody<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> i,<xref:System.Xml.XmlDocument> które umożliwiają wstawianie wartości dla węzła do obiektu. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
### <a name="inserting-untyped-values"></a>Wstawianie wartości niewpisanych  
 Metoda po prostu wstawia `string` wartość bez typu jako parametr jako wartość węzła, na którym <xref:System.Xml.XPath.XPathNavigator> znajduje się obiekt. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jest używana do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Wstawianie wpisanych wartości  
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger`), powoduje wyjątek.  
  
 Poniższy przykład próbuje `price` zmienić wartość elementu pierwszego `book` elementu <xref:System.DateTime> w `contosoBooks.xml` pliku na wartość. Ponieważ typ `price` schematu XML elementu jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` plikach, spowoduje to wyjątek.  
  
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
  
 Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Właściwości InnerXml i OuterXml  
 Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy zmieniają znaczniki XML w węzłach, w których obiektjestobecnieumieszczony.<xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator>  
  
 Właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string`. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych, w których obiekt jest obecnie umieszczony, a także bieżący węzeł.  
  
 Poza metodami opisanymi w tym temacie, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> właściwości i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą służyć do wstawiania węzłów i wartości w dokumencie XML. Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> używania <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości i do wstawiania węzłów i wartości, zobacz temat [modyfikowanie danych XML przy użyciu elementu XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="namespace-and-xmllang-conflicts"></a>Przestrzeń nazw i XML: konflikty lang  
 Niektóre konflikty związane z zakresem przestrzeni nazw `xml:lang` i deklaracji mogą wystąpić podczas wstawiania danych XML <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>przy użyciu <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>metod <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> , <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i metody <xref:System.Xml.XPath.XPathNavigator> klasy, która przyjmuje <xref:System.Xml.XmlReader>obiekty jako parametry.  
  
 Poniżej wymieniono potencjalne konflikty przestrzeni nazw.  
  
- Jeśli w kontekście <xref:System.Xml.XmlReader> obiektu znajduje się przestrzeń nazw, w której prefiks do mapowania identyfikatora URI przestrzeni nazw nie znajduje się <xref:System.Xml.XPath.XPathNavigator> w kontekście obiektu, zostanie dodana nowa Deklaracja przestrzeni nazw do nowo wstawionego węzła.  
  
- Jeśli ten sam identyfikator URI przestrzeni nazw znajduje się w zakresie zarówno <xref:System.Xml.XmlReader> w kontekście obiektu, <xref:System.Xml.XPath.XPathNavigator> jak i kontekście obiektu, ale ma inny prefiks mapowany na niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, z prefiksem i identyfikator URI przestrzeni nazw pobrany <xref:System.Xml.XmlReader> z obiektu.  
  
- Jeśli ten sam prefiks przestrzeni nazw znajduje się w zakresie zarówno <xref:System.Xml.XmlReader> w kontekście obiektu, <xref:System.Xml.XPath.XPathNavigator> jak i kontekście obiektu, ale ma inny identyfikator URI przestrzeni nazw mapowany do niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, który redeklaruje ten prefiks przy użyciu identyfikatora URI przestrzeni nazw <xref:System.Xml.XmlReader> pobranego z obiektu.  
  
- Jeśli prefiks <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> oraz identyfikator URI przestrzeni nazw w kontekście obiektu i kontekście obiektu są takie same, do nowo wstawionego węzła nie zostanie dodana żadna Nowa deklaracja przestrzeni nazw.  
  
> [!NOTE]
> Powyższy opis dotyczy również deklaracji przestrzeni nazw z pustym `string` prefiksem (na przykład deklaracji domyślnej przestrzeni nazw).  
  
 Możliwe `xml:lang` są następujące konflikty.  
  
- Jeśli `xml:lang` istnieje atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> w kontekście obiektu, ale nie w kontekście obiektu, `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawionego węzła.  
  
- Jeśli `xml:lang` istnieje atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> zarówno w kontekście obiektu, jak i kontekście obiektu, `xml:lang` ale każdy z nich ma inną wartość, atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawiony węzeł.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie <xref:System.Xml.XmlReader> zarówno w kontekście <xref:System.Xml.XPath.XPathNavigator> obiektu, jak i kontekstu obiektu, ale każdy z tą samą wartością, żaden nowy `xml:lang` atrybut nie zostanie dodany do nowo wstawionego węzła.  
  
- Jeśli istnieje `xml:lang` atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> w kontekście obiektu, <xref:System.Xml.XmlReader> ale żaden istniejący w kontekście obiektu nie `xml:lang` zostanie dodany do nowo wstawionego węzła.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Wstawianie węzłów z XmlWriter  
 Metody służące do wstawiania elementów równorzędnych, podrzędnych i atrybutów, które opisano w sekcji "Wstawianie węzłów i wartości" są przeciążone. <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Metody ,<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, iklasy<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> zwracają obiektużywany<xref:System.Xml.XmlWriter> do wstawiania węzłów. <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
### <a name="unsupported-xmlwriter-methods"></a>Nieobsługiwane metody XmlWriter  
 Nie wszystkie metody służące do zapisywania informacji w dokumencie XML przy użyciu <xref:System.Xml.XmlWriter> klasy są obsługiwane <xref:System.Xml.XPath.XPathNavigator> przez klasę z powodu różnic między modelem danych XPath a Document Object Model (dom).  
  
 W poniższej tabeli opisano <xref:System.Xml.XmlWriter> metody klasy, które nie są <xref:System.Xml.XPath.XPathNavigator> obsługiwane przez klasę.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<xref:System.NotSupportedException> Zgłasza wyjątek.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorowany na poziomie głównym i zgłasza wyjątek <xref:System.NotSupportedException> , jeśli jest wywoływana na dowolnym innym poziomie dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.|  
  
 Więcej informacji o <xref:System.Xml.XmlWriter> klasie można znaleźć w <xref:System.Xml.XmlWriter> dokumentacji dotyczącej klas.  
  
### <a name="multiple-xmlwriter-objects"></a>Wiele obiektów XmlWriter  
 Istnieje możliwość, że wiele <xref:System.Xml.XPath.XPathNavigator> obiektów wskazuje różne części dokumentu XML z co najmniej jednym otwartym <xref:System.Xml.XmlWriter> obiektem. Wiele <xref:System.Xml.XmlWriter> obiektów jest dozwolonych i obsługiwanych w scenariuszach wielowątkowych.  
  
 Poniżej znajdują się ważne uwagi, które należy wziąć <xref:System.Xml.XmlWriter> pod uwagę podczas korzystania z wielu obiektów.  
  
- Fragmenty XML zapisywane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do dokumentu XML, <xref:System.Xml.XmlWriter.Close%2A> gdy wywoływana jest metoda każdego <xref:System.Xml.XmlWriter> obiektu. Do tego <xref:System.Xml.XmlWriter> momentu obiekt zapisuje odłączony fragment. Jeśli operacja jest wykonywana na dokumencie XML, nie ma to wpływ na wszystkie fragmenty, <xref:System.Xml.XmlWriter> które są zapisywane przez <xref:System.Xml.XmlWriter.Close%2A> obiekt przed wywołaniem.  
  
- Jeśli istnieje otwarty <xref:System.Xml.XmlWriter> obiekt w określonym poddrzewie XML i że poddrzewo zostanie usunięte <xref:System.Xml.XmlWriter> , obiekt może nadal dodawać do poddrzewa. Poddrzewo po prostu zostaje usuniętym fragmentem.  
  
- Jeśli wiele <xref:System.Xml.XmlWriter> obiektów jest otwartych w tym samym punkcie dokumentu XML, są one dodawane do dokumentu XML w kolejności, w <xref:System.Xml.XmlWriter> której obiekty są zamknięte, a nie w kolejności, w jakiej zostały otwarte.  
  
 Poniższy przykład <xref:System.Xml.XmlDocument> tworzy obiekt, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator> tworzy obiekt, a następnie używa obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> `books.xml` metodę w celu utworzenia struktury pierwszej książki w pliku. Przykład zapisuje go jako `book.xml` plik.  
  
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
 Zapisywanie zmian wprowadzonych <xref:System.Xml.XmlDocument> w obiekcie w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
