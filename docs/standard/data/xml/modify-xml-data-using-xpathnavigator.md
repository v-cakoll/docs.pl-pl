---
title: Modyfikowanie danych XML przy użyciu parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb31c2ea504472a8707d700ff84b8c367467b607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579122"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Modyfikowanie danych XML przy użyciu parametrem XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używane do modyfikowania węzły i wartości w dokumencie XML. Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są tylko do odczytu i próby użycia metody edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> obiektów wyników w <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji o tworzeniu można edytować <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Modyfikowanie węzłów  
 Prosta technika w przypadku zmiany wartości węzła jest użycie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
 W poniższej tabeli wymieniono wpływu tych metod na inny węzeł typów.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Zmienione dane|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Nieobsługiwane.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Zawartość elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Wartość atrybutu.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Zawartość tekstowa.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Zawartość, z wyłączeniem obiektu docelowego.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Zawartość komentarza.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Nie jest obsługiwane.|  
  
> [!NOTE]
>  Edytowanie <xref:System.Xml.XPath.XPathNodeType.Namespace> węzłów lub <xref:System.Xml.XPath.XPathNodeType.Root> węzeł nie jest obsługiwany.  
  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia również zestaw metody używane do wstawiania i usuwania węzłów. Aby uzyskać więcej informacji na temat Wstawianie i usuwanie węzłów z dokumentu XML, zobacz [wstawiania danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [Usuń danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) tematów.  
  
### <a name="modifying-untyped-values"></a>Modyfikowanie nieuwzględniające typów wartości  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia bez typu `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na. Wartość jest wstawiany bez dowolnego typu lub bez sprawdzenia, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli informacje o schemacie są dostępne.  
  
 W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Modyfikowanie typu wartości  
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
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Edytowanie danych XML jednoznacznie efekty  
 <xref:System.Xml.XPath.XPathNavigator> Klasy używa schematu W3C XML jako podstawa dla opisu jednoznacznie XML. Elementy i atrybuty mogą być adnotowany przy informacje typu, w zależności od sprawdzenia poprawności względem schematu W3C XML dokumentu. Elementy, które mogą zawierać innych elementów lub atrybutów są nazywane typów złożonych, gdy te, które mogą zawierać tylko zawartość tekstową są nazywane typów prostych.  
  
> [!NOTE]
>  Atrybuty mogą mieć tylko proste typy.  
  
 Element lub atrybut jest uznawana za schematu-ważność, jeśli odpowiada wszystkich reguł określonych do jego definicji typu. Element, który ma typ prosty `xs:int` musi zawierać liczbą z zakresu od -2147483648 do 2147483647 jest nieprawidłowy schemat. Dla typów złożonych schematu ważności element jest zależny od schematu ważność jej elementy podrzędne i atrybutów. W związku z tym jeśli element jest prawidłowy przed jego definicję typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe przed ich definicji typu. Podobnie jeśli nawet jednego z elementów podrzędnych atrybuty elementu jest nieprawidłowa w przypadku jego definicji typu lub ma nieznany ważności, element jest również nieprawidłowe lub ważności nieznany.  
  
 Biorąc pod uwagę, że ważności element jest zależny od ważności jego elementy podrzędne i atrybuty, albo modyfikacje spowodować zmiany ważności elementu, jeśli został wcześniej prawidłowy. W szczególności jeśli elementy podrzędne lub atrybuty elementu są wstawiane, zaktualizowane lub usunięte, ważność element staje się nieznany. To jest reprezentowana przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwości elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości ustawiany <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Ponadto w tym celu dokonuje kaskadowych do góry rekursywnie w dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (element nadrzędny, i tak dalej) staje się również nieznany.  
  
 Aby uzyskać więcej informacji na temat sprawdzania poprawności schematu i <xref:System.Xml.XPath.XPathNavigator> , zobacz [sprawdzanie poprawności schematu użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Modyfikowanie atrybutów  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody może służyć do modyfikowania węzłów bez typu i typu atrybutu, a także inne typy węzłów wymienionych w sekcji "Modyfikowanie węzłów".  
  
 Poniższy przykład umożliwia zmianę wartości `genre` atrybutu pierwszego `book` element `books.xml` pliku.  
  
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
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz sekcje "Modyfikowanie nieuwzględniające typów wartości" i "Modyfikowanie wpisane wartości".  
  
## <a name="innerxml-and-outerxml-properties"></a>Właściwości OuterXml i InnerXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy Zmień adiustację XML węzłów <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na przy użyciu analizowanej zawartości danego XML `string`. Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na oraz bieżącego węzła.  
  
 W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość, aby zmodyfikować wartość `price` elementu i Wstaw nowy `discount` atrybutu pierwszego `book` element `contosoBooks.xml` pliku.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Modyfikowanie Namespace węzłów  
 W modelu DOM (Document Object), deklaracje przestrzeni nazw są traktowane jak, jeśli są one prawidłowe atrybuty, które można wstawiać, aktualizowane i usuwane. <xref:System.Xml.XPath.XPathNavigator> Klasa nie zezwala na takich operacji w węzłach przestrzeni nazw nie zmieniając wartość węzła przestrzeni nazw można zmienić tożsamości elementów i atrybutów w zakresie przestrzeń nazw, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Jeśli w powyższym przykładzie XML została zmieniona w następujący sposób, to skutecznie zmienia nazwę każdego elementu w dokumencie ponieważ wartość każdego elementu identyfikator URI przestrzeni nazw zostanie zmieniona.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Wstawianie węzłów przestrzeni nazw, które nie są w konflikcie z deklaracji przestrzeni nazw w zakresie, które zostały wstawione jest dozwolona przez <xref:System.Xml.XPath.XPathNavigator> klasy. W takim przypadku deklaracje przestrzeni nazw nie są zadeklarowane w dolnym zakresów w dokumencie XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Jeśli w powyższym przykładzie XML została zmieniona w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane przez dokumentu XML poniżej zakresu deklaracji przestrzeni nazw.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 W przykładzie XML powyżej atrybut `a:parent-id` jest wstawiane na `parent` element `http://www.contoso.com/parent-id` przestrzeni nazw. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda służy do wstawiania atrybutu, gdy znajduje się na `parent` elementu. `http://www.contoso.com` Deklaracji przestrzeni nazw jest automatycznie wstawiane przez <xref:System.Xml.XPath.XPathNavigator> klasy w celu zachowania spójności pozostałej części dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Modyfikowanie węzłów odwołanie do jednostki  
 Węzły odwołanie do jednostki w <xref:System.Xml.XmlDocument> obiektu są tylko do odczytu i nie można edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode> klasy. Wszelkie próby zmodyfikowania jednostki węzeł odniesienia powoduje <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Modyfikowanie xsi: nil węzłów  
 Zalecenie schematu W3C XML pojęcia związane z elementu trwa może być zerowy. Gdy element jest nillable, istnieje możliwość dla elementu, aby nie ma zawartości i nadal ważne. Koncepcja jest nillable elementu jest podobny do koncepcji jest obiekt `null`. Główną różnicą jest to, że `null` obiekt nie może być dostępne w dowolny sposób, podczas gdy `xsi:nil` element nadal ma właściwości, takie jak atrybuty, które są dostępne, ale nie ma zawartości (elementy podrzędne lub tekst). Istnienie `xsi:nil` atrybutu o wartości `true` elementu w pliku XML dokumentu służy do wskazywania, że element nie ma zawartości.  
  
 Jeśli <xref:System.Xml.XPath.XPathNavigator> obiekt jest używany w celu dodania zawartości do prawidłowego elementu z `xsi:nil` atrybutu o wartości `true`, wartość jego `xsi:nil` atrybut ma ustawioną `false`.  
  
> [!NOTE]
>  Jeśli zawartość elementu z `xsi:nil` ustawić atrybutu `false` jest usunięte, wartość atrybutu nie jest zmieniana na `true`.  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian <xref:System.Xml.XmlDocument> obiekt jako wynik edycji metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy. Aby uzyskać więcej informacji na temat zapisywania zmian w <xref:System.Xml.XmlDocument> obiektów, zobacz [zapisywania i zapisywanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
