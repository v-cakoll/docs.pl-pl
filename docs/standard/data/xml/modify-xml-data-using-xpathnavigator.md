---
title: Modyfikowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72cbcf1294f3d13f406d8db177f66fdc367c0758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724450"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Modyfikowanie danych XML przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które służy do modyfikowania węzłów i wartości w dokumencie XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być niemożliwa, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są przeznaczone tylko do odczytu i dowolne próba należy użyć metod edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> wynik w obiekcie <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu edytowalne <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Modyfikowanie węzłów  
 Proste techniki, w przypadku zmiany wartości węzła jest użycie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
 W poniższej tabeli wymieniono wpływu tych metod na różnych typów węzłów.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Zmiany danych|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Nieobsługiwane.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Zawartość elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Wartość atrybutu.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Zawartość tekstowa.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Zawartość, z wyłączeniem element docelowy.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Treść komentarza.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Nie jest obsługiwane.|  
  
> [!NOTE]
>  Edytowanie <xref:System.Xml.XPath.XPathNodeType.Namespace> węzłów lub <xref:System.Xml.XPath.XPathNodeType.Root> węzeł nie jest obsługiwany.  
  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia także zestaw metod używanych do wstawiania i usuwania węzłów. Aby uzyskać więcej informacji dotyczących wstawiania i usuwania węzłów z dokumentu XML, zobacz [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) tematów.  
  
### <a name="modifying-untyped-values"></a>Modyfikowanie wartości bez typu  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia nietypizowane `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na. Wartość jest wstawiany bez dowolnego typu lub bez weryfikacji, nowa wartość jest nieprawidłowa według typu węzła, jeśli informacje schematu są dostępne.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Modyfikowanie wartości Typizowane  
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
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Edytowanie danych XML w silnie Typizowany efektów  
 <xref:System.Xml.XPath.XPathNavigator> Klasa używa schematu XML W3C jako podstawy do opisywania silnie typizowane XML. Atrybuty i elementy mogą być adnotowane przy użyciu informacji o typie oparte na weryfikacji względem dokumentów schematu XML W3C. Elementy, które mogą zawierać innych elementów lub atrybutów są nazywane typów złożonych, gdy te, które mogą zawierać tylko zawartości tekstowej są nazywane typów prostych.  
  
> [!NOTE]
>  Atrybuty może mieć tylko proste typy.  
  
 Element lub atrybut jest uznawana za schematu-ważności, jeśli odpowiada wszystkie reguły specyficzne dla swojej definicji typu. Element, który ma typ prosty `xs:int` musi zawierać wartość liczbową od -2147483648 do 2147483647 był prawidłowy schemat. W przypadku typów złożonych poprawność schematu elementu jest zależna od schematu ważność jego elementów podrzędnych i atrybutów. Dlatego jeśli element jest nieprawidłowa względem jego definicji typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe przed ich definicje typów. Podobnie, jeśli jeszcze jeden z elementów podrzędnych atrybuty elementu jest nieprawidłowa w przypadku jej definicja typu lub ma nieznany ważności, element jest również niepoprawna lub nieznana ważność.  
  
 Biorąc pod uwagę, że ważność elementu jest zależny od ważności jego elementów podrzędnych i atrybutów, albo modyfikacje spowodować zmianę ważności elementu, jeśli została poprzednio prawidłowe. W szczególności jeśli elementy podrzędne i atrybuty elementu są wstawione, zaktualizowane lub usunięto, ważność element staje się nieznane. To jest reprezentowany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość zostanie ustawiona <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Ponadto w tym celu dokonuje kaskadowych do góry cyklicznie w dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (i jego element nadrzędny i tak dalej) staje się również nieznany.  
  
 Aby uzyskać więcej informacji na temat sprawdzania poprawności schematu i <xref:System.Xml.XPath.XPathNavigator> klasy, zobacz [sprawdzanie poprawności schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Modyfikowanie atrybutów  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody może służyć do modyfikowania węzłów atrybutu bez typu i kontrolą typów, a także inne typy węzłów wymienionych w sekcji "Modyfikowanie węzły".  
  
 Poniższy przykład zmienia wartość `genre` atrybut pierwszego `book` element `books.xml` pliku.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zapoznaj się z sekcjami "Modyfikowanie bez typu" oraz "Modyfikowanie wpisane wartości".  
  
## <a name="innerxml-and-outerxml-properties"></a>Właściwości OuterXml i elementu  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zmienić węzłów znaczniki XML <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> przeanalizowany zawartość XML danego obiektu aktualnie jest ustawiony na `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiektu aktualnie jest ustawiony na oraz bieżącego węzła.  
  
 W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość, aby zmodyfikować wartość `price` elementu i Wstaw nowy `discount` atrybut pierwszego `book` element `contosoBooks.xml` pliku.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
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
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Modyfikowanie węzłów Namespace  
 W modelu DOM (Document Object), deklaracje przestrzeni nazw są traktowane tak, jakby są regularnie atrybutów, które można wstawić, aktualizowane oraz usuwane. <xref:System.Xml.XPath.XPathNavigator> Klasy nie zezwala na takie operacje na węzły przestrzeni nazw, ponieważ zmiany wartości węzła obszaru nazw można zmienić tożsamości elementów i atrybutów w zakresie węzła obszaru nazw, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Jeśli w powyższym przykładzie XML zostanie zmieniony w następujący sposób, to skutecznie zmienia nazwę każdego elementu w dokumencie, ponieważ wartość identyfikatora URI obszaru nazw każdego elementu zostanie zmieniona.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Wstawianie węzły przestrzeni nazw, które nie wchodzą w konflikt z nazw deklaracji w zakresie, które zostały wstawione jest dozwolona przez <xref:System.Xml.XPath.XPathNavigator> klasy. W takim przypadku deklaracje przestrzeni nazw nie są zadeklarowane na niższe zakresy w dokumencie XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Jeśli w powyższym przykładzie XML zostanie zmieniony w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane w dokumencie XML poniżej zakresu deklaracji przestrzeni nazw.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 W przykładzie XML powyżej atrybut `a:parent-id` jest wstawiany na `parent` element `http://www.contoso.com/parent-id` przestrzeni nazw. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda służy do wstawiania atrybutu, gdy ustawiony na `parent` elementu. `http://www.contoso.com` Deklarację przestrzeni nazw jest automatycznie wstawiany przez <xref:System.Xml.XPath.XPathNavigator> klasy w celu zachowania spójności w pozostałej części dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Modyfikowanie węzłów odwołanie do jednostki  
 Węzły odwołanie do jednostki w <xref:System.Xml.XmlDocument> obiektu są przeznaczone tylko do odczytu i nie można edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode> klasy. Każda próba zmodyfikowania węzła odwołanie do obiektu skutkuje <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Modyfikowanie xsi: nil węzłów  
 Zaleceniem schematu XML W3C pojęcia związane z elementu trwa może być zerowy. Gdy element jest może być zerowy, jest możliwe dla elementu nie ma zawartości i nadal ważne. Pojęcia są może być zerowy element jest podobny do koncepcji jest obiekt `null`. Główną różnicą jest to, że `null` obiekt nie może być używane w jakikolwiek sposób, podczas gdy `xsi:nil` element nadal ma właściwości, takie jak atrybuty, które są dostępne, ale nie ma zawartości (elementy podrzędne lub tekst). Istnienie `xsi:nil` atrybutu o wartości `true` elementu w pliku XML dokumentu jest używany do wskazania, że element nie ma zawartości.  
  
 Jeśli <xref:System.Xml.XPath.XPathNavigator> obiekt jest używany do dodawania zawartości do prawidłowego elementu z `xsi:nil` atrybutu o wartości `true`, wartość jego `xsi:nil` ma ustawioną wartość atrybutu `false`.  
  
> [!NOTE]
>  Jeśli zawartość elementu za pomocą `xsi:nil` ustawioną wartość atrybutu `false` jest usunięte, wartość atrybutu nie jest zmieniana na `true`.  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiektu jako wynik edycji metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian <xref:System.Xml.XmlDocument> obiektu, zobacz [zapisywania i zapisywania dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
