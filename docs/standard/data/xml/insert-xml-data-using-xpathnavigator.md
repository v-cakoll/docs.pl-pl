---
title: Wstawianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710729"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Wstawianie danych XML przy użyciu klasy XPathNavigator
Klasa <xref:System.Xml.XPath.XPathNavigator> zawiera zestaw metod służących do wstawiania węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Aby można było korzystać z tych metod, obiekt <xref:System.Xml.XPath.XPathNavigator> musi być edytowalny, oznacza to, że jego właściwość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiektów, które mogą edytować dokument XML, są tworzone przez metodę <xref:System.Xml.XmlDocument.CreateNavigator%2A> klasy <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> obiektów utworzonych przez klasę <xref:System.Xml.XPath.XPathDocument> są tylko do odczytu, a każda próba użycia metod edycji obiektu <xref:System.Xml.XPath.XPathNavigator> utworzonego przez obiekt <xref:System.Xml.XPath.XPathDocument> powoduje <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji na temat tworzenia edytowalnych obiektów <xref:System.Xml.XPath.XPathNavigator>, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Wstawianie węzłów  
 Klasa <xref:System.Xml.XPath.XPathNavigator> zapewnia metody wstawiania węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML. Te metody umożliwiają wstawianie węzłów i atrybutów w różnych lokalizacjach w odniesieniu do bieżącego położenia obiektu <xref:System.Xml.XPath.XPathNavigator> i są opisane w poniższych sekcjach.  
  
### <a name="inserting-sibling-nodes"></a>Wstawianie węzłów równorzędnych  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia następujące metody wstawiania węzłów równorzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Te metody wstawiają węzły równorzędne przed i po węźle, w którym jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody są przeciążone i akceptują `string`, <xref:System.Xml.XmlReader> obiekt lub obiekt <xref:System.Xml.XPath.XPathNavigator> zawierający węzeł równorzędny do dodania jako parametry. Obie metody zwracają również obiekt <xref:System.Xml.XmlWriter> używany do wstawiania węzłów elementów równorzędnych.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> wstawiają pojedynczy węzeł równorzędny przed i po węźle, w którym obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie nowy element `pages` jest wstawiany przed `price` elementem podrzędnym pierwszego `book` elementu w pliku `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o metodach <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-child-nodes"></a>Wstawianie węzłów podrzędnych  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia następujące metody wstawiania węzłów podrzędnych.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Te metody dołączą i dołączają węzły podrzędne do końca i początku listy węzłów podrzędnych węzła, w którym jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
 Podobnie jak metody w sekcji "Wstawianie węzłów równorzędnych", metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> akceptują `string`, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł podrzędny, aby dodać jako parametry. Obie metody zwracają również obiekt <xref:System.Xml.XmlWriter> używany do wstawiania węzłów podrzędnych.  
  
 Podobnie jak metody w sekcji "Wstawianie węzłów równorzędnych", metody <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> umożliwiają wstawianie jednego węzła podrzędnego do końca i początku listy węzłów podrzędnych węzła, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.  
  
 W poniższym przykładzie do listy elementów podrzędnych pierwszego elementu `book` w pliku `contosoBooks.xml` jest dołączany nowy element podrzędny `pages`.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Więcej informacji o metodach <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-attribute-nodes"></a>Wstawianie węzłów atrybutów  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia następujące metody wstawiania węzłów atrybutów.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Te metody wstawiają węzły atrybutów w węźle elementu, w którym jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>. Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> tworzy węzeł atrybutu w węźle elementu, <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry. Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> zwraca obiekt <xref:System.Xml.XmlWriter> używany do wstawiania węzłów atrybutów.  
  
 W poniższym przykładzie są tworzone nowe atrybuty `discount` i `currency` w elemencie podrzędnym `price` pierwszego elementu `book` w `contosoBooks.xml` pliku przy użyciu obiektu <xref:System.Xml.XmlWriter> zwróconego z metody <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Aby uzyskać więcej informacji na temat metod <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>, zobacz dokumentację dotyczącą klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="copying-nodes"></a>Kopiowanie węzłów  
 W niektórych przypadkach może być konieczne wypełnienie dokumentu XML zawartością z innego dokumentu XML. Zarówno Klasa <xref:System.Xml.XPath.XPathNavigator>, jak i Klasa <xref:System.Xml.XmlWriter> mogą kopiować węzły do obiektu <xref:System.Xml.XmlDocument> z istniejącego obiektu <xref:System.Xml.XmlReader> lub obiektu <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody klasy <xref:System.Xml.XPath.XPathNavigator> mają przeciążenia, które mogą akceptować obiekt <xref:System.Xml.XPath.XPathNavigator> lub obiekt <xref:System.Xml.XmlReader> jako parametr.  
  
 Metoda <xref:System.Xml.XmlWriter.WriteNode%2A> klasy <xref:System.Xml.XmlWriter> ma przeciążenia, które mogą akceptować obiekt <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>lub <xref:System.Xml.XPath.XPathNavigator>.  
  
 Poniższy przykład kopiuje wszystkie elementy `book` z jednego dokumentu do drugiego.  
  
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
 Klasa <xref:System.Xml.XPath.XPathNavigator> dostarcza metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, aby wstawić wartości dla węzła do obiektu <xref:System.Xml.XmlDocument>.  
  
### <a name="inserting-untyped-values"></a>Wstawianie wartości niewpisanych  
 Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> po prostu wstawia wartość nietypu `string` przekazaną jako parametr jako wartość węzła, w którym obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony. Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.  
  
 W poniższym przykładzie metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> służy do aktualizowania wszystkich elementów `price` w pliku `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Wstawianie wpisanych wartości  
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez metodę <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` dla elementu, którego typem jest `xs:positiveInteger`), powoduje wyjątek.  
  
 Poniższy przykład próbuje zmienić wartość elementu `price` pierwszego elementu `book` w pliku `contosoBooks.xml` na wartość <xref:System.DateTime>. Ponieważ typ schematu XML elementu `price` jest zdefiniowany jako `xs:decimal` w plikach `contosoBooks.xsd`, spowoduje to wyjątek.  
  
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
 Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy <xref:System.Xml.XPath.XPathNavigator> zmieniają znaczniki XML dla węzłów, w których jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
 Właściwość <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony w przeanalizowanej zawartości danego `string`XML. Podobnie Właściwość <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony, a także bieżący węzeł.  
  
 Poza metodami opisanymi w tym temacie właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą służyć do wstawiania węzłów i wartości w dokumencie XML. Aby uzyskać więcej informacji na temat używania właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> do wstawiania węzłów i wartości, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="namespace-and-xmllang-conflicts"></a>Przestrzeń nazw i XML: konflikty lang  
 Niektóre konflikty związane z zakresem przestrzeni nazw i deklaracji `xml:lang` mogą wystąpić podczas wstawiania danych XML przy użyciu metod <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> klasy <xref:System.Xml.XPath.XPathNavigator>, które pobierają <xref:System.Xml.XmlReader> obiekty jako parametry.  
  
 Poniżej wymieniono potencjalne konflikty przestrzeni nazw.  
  
- Jeśli w kontekście obiektu <xref:System.Xml.XmlReader> istnieje przestrzeń nazw, w której Prefiks mapowania identyfikatora URI w przestrzeni nazw nie znajduje się w kontekście obiektu <xref:System.Xml.XPath.XPathNavigator>, zostanie dodana nowa Deklaracja przestrzeni nazw do nowo wstawionego węzła.  
  
- Jeśli ten sam identyfikator URI przestrzeni nazw występuje w zakresie zarówno w kontekście obiektu <xref:System.Xml.XmlReader>, jak i w kontekście obiektu <xref:System.Xml.XPath.XPathNavigator>, ale ma inny prefiks mapowany do niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, z prefiksem i identyfikatorem URI przestrzeni nazw pobranym z obiektu <xref:System.Xml.XmlReader>.  
  
- Jeśli ten sam prefiks przestrzeni nazw znajduje się w zakresie zarówno w kontekście obiektu <xref:System.Xml.XmlReader>, jak i w kontekście obiektu <xref:System.Xml.XPath.XPathNavigator>, ale ma inny identyfikator URI przestrzeni nazw zmapowany do niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, który ponownie deklaruje ten prefiks z identyfikatorem URI przestrzeni nazw pobranym z obiektu <xref:System.Xml.XmlReader>.  
  
- Jeśli prefiks oraz identyfikator URI przestrzeni nazw zarówno w kontekście obiektu <xref:System.Xml.XmlReader>, jak i kontekście obiektu <xref:System.Xml.XPath.XPathNavigator> jest taka sama, nie zostanie dodana nowa Deklaracja przestrzeni nazw do nowo wstawionego węzła.  
  
> [!NOTE]
> Powyższy opis dotyczy również deklaracji przestrzeni nazw z pustą `string` jako prefiks (na przykład domyślna Deklaracja przestrzeni nazw).  
  
 Poniżej przedstawiono możliwe `xml:lang` konfliktów.  
  
- Jeśli istnieje atrybut `xml:lang` w zakresie w kontekście obiektu <xref:System.Xml.XmlReader>, ale nie w kontekście <xref:System.Xml.XPath.XPathNavigator> obiektu, atrybut `xml:lang`, którego wartość jest pobierana z obiektu <xref:System.Xml.XmlReader> zostanie dodany do nowo wstawionego węzła.  
  
- Jeśli istnieje atrybut `xml:lang` w zakresie zarówno w kontekście obiektu <xref:System.Xml.XmlReader>, jak i kontekstu <xref:System.Xml.XPath.XPathNavigator> obiektu, ale każdy z nich ma inną wartość, atrybut `xml:lang`, którego wartość jest pobierana z obiektu <xref:System.Xml.XmlReader> zostanie dodany do nowo wstawionego węzła.  
  
- Jeśli istnieje atrybut `xml:lang` w zakresie zarówno w kontekście obiektu <xref:System.Xml.XmlReader>, jak i kontekstu <xref:System.Xml.XPath.XPathNavigator> obiektu, ale każdy z tą samą wartością, żaden nowy atrybut `xml:lang` nie zostanie dodany do nowo wstawionego węzła.  
  
- Jeśli istnieje atrybut `xml:lang` w zakresie w kontekście obiektu <xref:System.Xml.XPath.XPathNavigator>, ale żadna istniejąca w kontekście <xref:System.Xml.XmlReader> obiektu `xml:lang` nie zostanie dodana do nowo wstawionego węzła.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Wstawianie węzłów z XmlWriter  
 Metody służące do wstawiania elementów równorzędnych, podrzędnych i atrybutów, które opisano w sekcji "Wstawianie węzłów i wartości" są przeciążone. Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> klasy <xref:System.Xml.XPath.XPathNavigator> zwracają obiekt <xref:System.Xml.XmlWriter> używany do wstawiania węzłów.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nieobsługiwane metody XmlWriter  
 Nie wszystkie metody służące do zapisywania informacji w dokumencie XML przy użyciu klasy <xref:System.Xml.XmlWriter> są obsługiwane przez klasę <xref:System.Xml.XPath.XPathNavigator> z powodu różnicy między modelem danych XPath a Document Object Model (DOM).  
  
 W poniższej tabeli opisano metody klasy <xref:System.Xml.XmlWriter> nieobsługiwane przez klasę <xref:System.Xml.XPath.XPathNavigator>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Zgłasza wyjątek <xref:System.NotSupportedException>.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorowany na poziomie głównym i zgłasza wyjątek <xref:System.NotSupportedException>, jeśli jest wywoływana na dowolnym innym poziomie dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Traktowane jako wywołanie metody <xref:System.Xml.XmlWriter.WriteString%2A> odpowiadającego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Traktowane jako wywołanie metody <xref:System.Xml.XmlWriter.WriteString%2A> odpowiadającego znaku lub znaków.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Traktowane jako wywołanie metody <xref:System.Xml.XmlWriter.WriteString%2A> odpowiadającego znaku lub znaków.|  
  
 Więcej informacji na temat klasy <xref:System.Xml.XmlWriter> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.XmlWriter>.  
  
### <a name="multiple-xmlwriter-objects"></a>Wiele obiektów XmlWriter  
 Istnieje możliwość, że wiele obiektów <xref:System.Xml.XPath.XPathNavigator> wskazuje różne części dokumentu XML z co najmniej jednym otwartym obiektem <xref:System.Xml.XmlWriter>. Wiele obiektów <xref:System.Xml.XmlWriter> jest dozwolonych i obsługiwanych w scenariuszach wielowątkowych.  
  
 Poniżej znajdują się ważne uwagi, które należy wziąć pod uwagę podczas korzystania z wielu <xref:System.Xml.XmlWriter> obiektów.  
  
- Fragmenty XML zapisywane przez obiekty <xref:System.Xml.XmlWriter> są dodawane do dokumentu XML, gdy wywoływana jest metoda <xref:System.Xml.XmlWriter.Close%2A> każdego obiektu <xref:System.Xml.XmlWriter>. Do tego momentu obiekt <xref:System.Xml.XmlWriter> zapisuje odłączony fragment. Jeśli operacja jest wykonywana na dokumencie XML, wszystkie fragmenty, które są zapisywane przez obiekt <xref:System.Xml.XmlWriter> przed wywołaniem <xref:System.Xml.XmlWriter.Close%2A>, nie mają na to wpływ.  
  
- Jeśli istnieje otwarty obiekt <xref:System.Xml.XmlWriter> w określonym poddrzewie XML i że poddrzewo zostanie usunięte, obiekt <xref:System.Xml.XmlWriter> nadal może zostać dodany do poddrzewa. Poddrzewo po prostu zostaje usuniętym fragmentem.  
  
- Jeśli wiele obiektów <xref:System.Xml.XmlWriter> jest otwartych w tym samym punkcie dokumentu XML, są one dodawane do dokumentu XML w kolejności, w której obiekty <xref:System.Xml.XmlWriter> są zamknięte, a nie w kolejności, w jakiej zostały otwarte.  
  
 Poniższy przykład tworzy obiekt <xref:System.Xml.XmlDocument>, tworzy obiekt <xref:System.Xml.XPath.XPathNavigator>, a następnie używa obiektu <xref:System.Xml.XmlWriter> zwróconego przez metodę <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> do tworzenia struktury pierwszej książki w pliku `books.xml`. Następnie przykład zapisuje go jako plik `book.xml`.  
  
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
 Zapisywanie zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument> w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod klasy <xref:System.Xml.XmlDocument>. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument>, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
